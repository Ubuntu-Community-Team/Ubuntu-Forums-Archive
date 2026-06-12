---
title: "Cant install rarlinux . I want my rar files !!!!!!!"
date: 2006-03-15
forum: Absolute Beginner Talk
---

### Post by subwr on 2006-03-15
:rolleyes: 
Well i ve read lots of threads of how to install any program to unrar my files but i didnt managed to do anything. I am quite a n00b in linux.
I ve downloaded rarlinux-3.3.0.tar.gr and as im used of winxp i double klicked on it. i can see the files but i dont know kow to install them. I think that i must put rar and unrar files on bin dir but the system tells me that i dont have access to do it. I just installed linux and i made only my account. Is there any administrator account and if yes what is the password? I tryed with the pass of my account and didnt work.

Where can i find a program that unrar files with full explation of how to do it?

---

### Post by frodon on 2006-03-15
"rar" allow to unrar the rar archives, also try a right click on your rar archive you should have an option like "extract here".
About your root password you should read that : [https://wiki.ubuntu.com/RootSudo?](https://wiki.ubuntu.com/RootSudo?)

---

### Post by Jucato on 2006-03-15
actually, "unrar" is the package for decompressing rar archives, and "rar" is the one for compressing into rar archives, AFAIK.
These are back-end programs, I believe.

---

### Post by mcduck on 2006-03-15
[QUOTE=subwr]:rolleyes: 
Well i ve read lots of threads of how to install any program to unrar my files but i didnt managed to do anything. I am quite a n00b in linux.
I ve downloaded rarlinux-3.3.0.tar.gr and as im used of winxp i double klicked on it. i can see the files but i dont know kow to install them. I think that i must put rar and unrar files on bin dir but the system tells me that i dont have access to do it. I just installed linux and i made only my account. Is there any administrator account and if yes what is the password? I tryed with the pass of my account and didnt work.

Where can i find a program that unrar files with full explation of how to do it?[/QUOTE]What you need is available in Ubuntu repositories, no need to download anything yourself :)

First, you need to enable Universe and Multiverse repos. Here's instructions how to do that: [http://www.psychocats.net/linux/sources.php]("http://www.psychocats.net/linux/sources.php").
After that, open a terminal (in Applications/Accessories/Terminal), type 'sudo apt-get update && sudo apt-get install rar unrar' and press enter.

Of course you could use Synaptic to install those packages too. (in System/Administration/Synaptic Package Manager)

You might want to read this too: [http://www.psychocats.net/linux/installingsoftware.php]("http://www.psychocats.net/linux/installingsoftware.php")

---

### Post by frodon on 2006-03-15
[QUOTE=Fenyx]actually, "unrar" is the package for decompressing rar archives, and "rar" is the one for compressing into rar archives, AFAIK.[/QUOTE]Yes but if you type : ```
rar e archive_name
```It will decompress your archive, it's what i use when i do it in terminal otherwise i use the right click under nautilus and the "extract here" tab.

---

