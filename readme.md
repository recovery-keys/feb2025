# Backup [15-feb-2025]
# Backup versions - L1 -> v7, L2 -> v3

## Combinations:
- read the `hints` provided.
- use the shared password manager to obtain the password.
- follow the steps in correct sequence.
- for key files use a text editor or the terminal:
```
cat keys/KEY_FILE
```
- generate the md5 using : 
```
md5sum images/FILE_NAME
```

## content generation process:

### images : 

- convert all the files to jpg/jpeg and remove png/bmp.
```
for i in *.png; do mogrify -format jpg "$i" ; done

rm *.png
rm *.bmp

```
- strip metadata:
``` 
for i in *; do exiftool -all= "$i" ; done
```
- remove original files:
```
rm *.*_original
```
- optimize the image files:
```
for i in *; do jpegoptim "$i" ; done
```
- randomize the image content
```
python3 image_randomizer /media/images/
```

### keys :
- generate random content of 32 characters as key files:
```
for i in {1..2040}; do LC_ALL=C tr -dc 'A-Za-z0-9!"#$%&'\''()*+,-./:;<=>?@[\]^_`{|}~' </dev/urandom | head -c 32  > $i.key; done
```

### git config when pushing changes:
```
git config user.name "teta2064"
git config user.email teta2064@outlook.com
git config credential.username teta2064@outlook.com
```

### tools
- mogrify
- exiftool
- jpegoptim
- image_randomizer

![alt text](https://raw.githubusercontent.com/recovery-keys/feb2025/refs/heads/main/fed-2025_flow.drawio.png)