---
title: "can someone tell me what this means?"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by jprice19 on 2008-04-04
What is this wanting me to do?
INSTALLATION

Now that everything is well set, we'll install the new theme. Fisrt of all copy the file contained in this directory, named 'usplash-theme-fingerprint.so' insto your Desktop. Now open a terminal and digit
		
		cd
		cd Desktop
		sudo cp usplash-theme-fingerprint.so /usr/lib/usplash
		sudo update-alternatives --install /usr/lib/usplash/usplash-artwork.so usplash-artwork.so /usr/lib/usplash/usplash-theme-fingerprint.so 10
		sudo update-alternatives --config usplash-artwork.so

And choose the righ value (write the number displayed near the file called 'usplash-theme-fingerprint.so' then press Return to confirm)

---

### Post by Tatty on 2008-04-04
open a terminal Applications->Accessories->Terminal, then type each line one after another.  Or you could copy and pase - which would be better to make sure you dont make typos.

---

### Post by Tyke91 on 2008-04-05
in case the OP was wondering whether any of the code was malicious:

```
cd
```change to your home directory
        ```
cd Desktop
```go to your desktop directory inside of home
        ```
sudo cp usplash-theme-fingerprint.so /usr/lib/usplash
```use administrative powers to copy that usplash theme into /usr/lib/usplash directory
        ```
sudo update-alternatives --install /usr/lib/usplash/usplash-artwork.so usplash-artwork.so /usr/lib/usplash/usplash-theme-fingerprint.so 10
```a script to install your new usplash theme
        ```
sudo update-alternatives --config usplash-artwork.so
```configure your new usplash theme to your system.

it's not malicious.

---

