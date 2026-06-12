---
title: "installing fonts for gimp 2.6"
date: 2009-01-29
forum: Art &amp; Design
---

### Post by menschtx on 2009-01-29
I have read the listings, and am told to search for <home/name/.fonts, the only one I have found is .fontconfig, I have done ctrl+h and the listing is replaced and then I don't see .fontconfig. I have copied the threads in order to keep trying, any suggestions. Ubuntu 8.10 and plenty of the other stuff.

---

### Post by kostkon on 2009-01-29
> **menschtx said:**
> I have read the listings, and am told to search for <home/name/.fonts, the only one I have found is .fontconfig, I have done ctrl+h and the listing is replaced and then I don't see .fontconfig. I have copied the threads in order to keep trying, any suggestions. Ubuntu 8.10 and plenty of the other stuff.
It is supposed to be a folder. Just create it yourself and put your fonts in there  ;)
i.e. create a folder named
```
.fonts
```
in your home folder.

Hope that helps.

---

### Post by menschtx on 2009-01-29
Ok I created a folder but with another name, so do I extract them to the folder and then to gimp, or is there folder inside of gimp 2.6?

---

### Post by kostkon on 2009-01-29
> **menschtx said:**
> Ok I created a folder but with another name, so do I extract them to the folder and then to gimp, or is there folder inside of gimp 2.6?
No, the folder must be named *.fonts* (and exist directly in your home folder) in order the system to see your fonts. After putting the fonts inside this folder, every application (including *Gimp*), will be able to see them.

---

### Post by smartboyathome on 2009-01-30
> **kostkon said:**
> No, the folder must be named *.fonts* (and exist directly in your home folder) in order the system to see your fonts. After putting the fonts inside this folder, every application (including *Gimp*), will be able to see them.

You might need to run fontconfig for some apps. :(

---

### Post by AJB2K3 on 2009-01-30
Ok I have a new tutorial on this in my sig VVVVVVV
Please have a read.

---

### Post by menschtx on 2009-01-31
> **kostkon said:**
> No, the folder must be named *.fonts* (and exist directly in your home folder) in order the system to see your fonts. After putting the fonts inside this folder, every application (including *Gimp*), will be able to see them.

I thank you - I believe it's working.

---

### Post by menschtx on 2009-01-31
> **AJB2K3 said:**
> Ok I have a new tutorial on this in my sig VVVVVVV
Please have a read.

I downloaded some .gbr and have them in gimp 2.6/brushes but when attempting to open get an error:there is no application installed for this file type. This folder is in the gimp 2.6 folder /home/michael/gimp 2.6/brushes. 
I have seen other tutorials with gimp -2.0/share/gimp/2.0/brushes< does /share/ - have to do with getting them into the folder?

---

### Post by menschtx on 2009-01-31
> **AJB2K3 said:**
> Ok I have a new tutorial on this in my sig VVVVVVV
Please have a read.
Went there: Sorry, the page you requested was not found

---

### Post by kostkon on 2009-01-31
> **menschtx said:**
> I downloaded some .gbr and have them in gimp 2.6/brushes but when attempting to open get an error:there is no application installed for this file type. This folder is in the gimp 2.6 folder /home/michael/gimp 2.6/brushes. 
I have seen other tutorials with gimp -2.0/share/gimp/2.0/brushes< does /share/ - have to do with getting them into the folder?
You don't need to open each of these files per se, just run Gimp and you should be able to use them from there.

Gimp will load them if they are in the right folder.

---

### Post by menschtx on 2009-02-01
> **smartboyathome said:**
> You might need to run fontconfig for some apps. :(
Ok smartboyathome, what is the purpose of running - run fontconfig, what is the purpose of fontconfig?

---

### Post by AJB2K3 on 2009-02-01
> **menschtx said:**
> Went there: Sorry, the page you requested was not found

Huh ?
[http://www.geocities.com/ajb2k305/tutorials/font.html]("http://www.geocities.com/ajb2k305/tutorials/font.html")
not found?

Anyone else have this problem access the site?
> **menschtx said:**
> Ok smartboyathome, what is the purpose of running - run fontconfig, what is the purpose of fontconfig?
I don't see a point in it.

---

