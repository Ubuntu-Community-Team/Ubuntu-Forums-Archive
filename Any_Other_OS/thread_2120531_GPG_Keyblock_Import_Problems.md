---
title: "GPG Keyblock Import Problems"
date: 2013-02-26
forum: Any Other OS
---

### Post by Creenome on 2013-02-26
copying my exact bash command

keith@Boss ~ $ gpg --import "key.txt"
gpg: can't open `key.txt': No such file or directory
gpg: Total number processed: 0


Ok so this worked perfectly fine about a week ago then all of a sudden wouldn't work. I tried a fresh install of linux 13 Maya and I still get the same error message.

The file DOES exist so I'm past that problem. I'm trying to import a keyblock to my keyring. I saved the keyblock as a .txt file just as the gnupg guide prompts. As i said, this exact method has worked fine in the past. It seems whenever I use a command in konsole that incorporates file paths, I get the same error "no such file or directory"

HELPPP

---

### Post by dcstar on 2013-02-26
> **Creenome said:**
> copying my exact bash command

keith@Boss ~ $ gpg --import "key.txt"
gpg: can't open `key.txt': No such file or directory
gpg: Total number processed: 0
.........

[LIST=1]
[*]What version of Ubuntu are you using?
[*]Provide the output of:
```
ls key.txt
```
[/LIST]

---

### Post by Creenome on 2013-02-26
> **dcstar said:**
> 
[LIST=1]
[*]What version of Ubuntu are you using?
[*]Provide the output of:
```
ls key.txt
```
[/LIST]

Im using Mint 13 Maya 3.2.0 x64
The output of ls reads the error
"ls: cannot access key.txt: No such file or directory"
But I assure you, I'm looking at the file right now.

---

### Post by Impavidus on 2013-02-27
Is it present in the right directory? If you type```
ls
```right before the```
gpg --import "key.txt"
```, does it show the file key.txt? If not, you should give the correct path, if it does, something funny may be going on with the file name, like non-printing characters being present.

---

### Post by Creenome on 2013-02-27
> **Impavidus said:**
> Is it present in the right directory? If you type```
ls
```right before the```
gpg --import "key.txt"
```, does it show the file key.txt? If not, you should give the correct path, if it does, something funny may be going on with the file name, like non-printing characters being present.
Well typing ```
ls
``` provides me with my home folders including "public keys" in which my key.txt file is located in.

I moved my "key.txt" into my home folder and ran  ```
ls
``` and my "key.txt" shows up also.

---

### Post by Impavidus on 2013-02-27
If the file "key.txt" is in the directory "public keys", you may need```
gpg --import "~/public keys/key.txt"
.
gpg --import "key.txt"
```would only work if the file were located in your current directory, the directory where you are in your terminal when calling gpg. Assuming gpg doesn't search, which it appears not to do.

---

### Post by Creenome on 2013-02-27
> **Impavidus said:**
> If the file "key.txt" is in the directory "public keys", you may need```
gpg --import "~/public keys/key.txt"
.
gpg --import "key.txt"
```would only work if the file were located in your current directory, the directory where you are in your terminal when calling gpg. Assuming gpg doesn't search, which it appears not to do.

Running the command as you point out also returns "no such file or directory"
Ive tried moving file locations and running konsole in the current directory as my "key.txt". 
Neither of these work.

---

### Post by Creenome on 2013-03-01
Bump

---

