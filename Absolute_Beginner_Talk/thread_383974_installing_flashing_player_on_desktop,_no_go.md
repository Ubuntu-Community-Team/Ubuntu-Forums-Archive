---
title: "installing flashing player on desktop, no go"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by warriore on 2007-03-13
dear ubuntu community, I have read your help docs, and the information i have obtained like to change directories using the cd, however, when I try to get the flash player installed which is located at home/ty/desktop/install_flash_player_9_linux 

all I can get to is /home$ with the cd .. command, but when i try to get to ty/desktop/... there after, it says no file or directory which makes no sense to me since it does exist 

as based on your help docs i use the following: 

 cd /ty/desktop/instal_flash_player_9_install 

am i doing somehting wrong?

thanks for your help,i hope I am not asking too much of this great community of ubuntu creators to take a minute and respond

---

### Post by halitech on 2007-03-13
Linux is case sensative, I believe the correct location is actually cd Desktop

---

### Post by lilchris173 on 2007-03-13
Agreed. Case Sensitive :-) Good Luck. And why do it by hand haha. [www.getautomatix.com](www.getautomatix.com) hehe Automatix does everything for ya.

---

### Post by aysiu on 2007-03-13
This should help you:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by warriore on 2007-03-13
cd Desktop   no worky either thanks for your efforts

---

### Post by aysiu on 2007-03-13
> **warriore said:**
> cd Desktop   no worky either thanks for your efforts
Just copy and paste the commands from the link I posted.

---

### Post by halitech on 2007-03-13
so right now you are at USERNAME@HOSTNAME and you want to go to desktop, it should be 

```

cd Desktop

```

question is, where do you have the file downloaded to?

---

### Post by slayerboy on 2007-03-13
> **warriore said:**
> dear ubuntu community, I have read your help docs, and the information i have obtained like to change directories using the cd, however, when I try to get the flash player installed which is located at home/ty/desktop/install_flash_player_9_linux 

all I can get to is /home$ with the cd .. command, but when i try to get to ty/desktop/... there after, it says no file or directory which makes no sense to me since it does exist 

as based on your help docs i use the following: 

 cd /ty/desktop/instal_flash_player_9_install 

am i doing somehting wrong?

thanks for your help,i hope I am not asking too much of this great community of ubuntu creators to take a minute and respond

This is not the correct way to change a directory.  You can either do this:

```
cd /home/ty/Desktop/install_flash_player_9_install
```or

```
cd /home
cd ty
cd Desktop
cd install_flash_player_9_install
```but if you were in /home and typed cd /ty it would look for /ty instead of /home/ty.

The cd command locates all relative from the root system (or "/").:)

Better yet, why not just install flash 9 from synaptic instead?  it's in the repos...

---

### Post by warriore on 2007-03-14
aysiu, the instructions on the site you gave me do not work, the first option with the single line command, no go, and the second option, that uses the wget gives error, no such host,,,

slayerboy and holitech; thanks guys for your efforts, i could swear that i tried it that way before and it did not work, but then, ah! i know the problem, the help dos tell you to type cd / and the directory name, but when i just did cd Desktop from the ty@ubuntu i finally got to the directory and the rest of it worked well I was able to get to the install file and stall it, thanks a lot....anyone here familliar with how to install webmin? 

lilchris173 thanks, but you refered me to a site that was just hacked and completely erased, i tell you its not a confidance builder to read that on the first page of something you want to use on your computer, anyways, if anyone lese has experience with automatix let me know if i should get that.  

thank you for your response, sincerely

ty

ty

---

### Post by bikeboy on 2007-03-14
Just a useful tip, when in the command line you can start typing and then press the "tab" key, it will help you autocomplete.

For example:
ty@ubuntu:~$ cd De [press tab]
ty@ubuntu:~$ cd Desktop/

---

### Post by warriore on 2007-03-14
thanks a lot, apreciate that.. some one here told me I can copy and paste commands I tried it and it does not work, is there a trick to it a setting I have to change to be able to do that? anyways, thanks a lot!

---

### Post by aysiu on 2007-03-14
> **warriore said:**
> thanks a lot, apreciate that.. some one here told me I can copy and paste commands I tried it and it does not work, is there a trick to it a setting I have to change to be able to do that? anyways, thanks a lot!
You can always do highlight and right-click.

The keyboard shortcut to paste into the terminal is Shift-Insert. Retyping is slow and prone to errors. Copy and paste is always the way to go.

---

### Post by 3rdalbum on 2007-03-14
There is a trick to it: When you copy or paste in the terminal, you should use the Edit menu rather than keyboard shortcuts.

---

### Post by warriore on 2007-03-14
thanks for the tip works like a charm

---

### Post by aysiu on 2007-03-14
> **3rdalbum said:**
> There is a trick to it: When you copy or paste in the terminal, you should use the Edit menu rather than keyboard shortcuts.
Mind if I ask what problems you've encountered with Shift-Insert? I've found that shortcut to pose no problems, but maybe there's something I don't know about?

---

