---
title: "having command issue with terminal"
date: 2006-05-09
forum: Absolute Beginner Talk
---

### Post by LipSkidr on 2006-05-09
I decided I would like to switch to Linux, I have just had enough of Microsoft and there over priced products ect..

A friend of mine suggested Ubuntu, so last night I installed it and so far color me impressed :KS .  Now I would like to learn to tweak it to my taste.

First I would love to upgrade the FireFox browser to the newest, my favourite theme will not load.  So I went to this site [http://www.psychocats.net/ubuntu/firefox]("http://www.psychocats.net/ubuntu/firefox")
and was following the instructions, but the first problem I have come across is that when I type "cd desktop" in the terminal I get the error below.

richard@home-96u1az6cer:~$ cd desktop
bash: cd: desktop: No such file or directory
richard@home-96u1az6cer:~$

I would love some advice on what I am doing wrong.

---

### Post by user1397 on 2006-05-09
you have to type 
```
cd Desktop
```
with a capital because linux recognizes a difference between upper-case and lower-case letters

---

### Post by LipSkidr on 2006-05-09
First off thank you for the quick reply :) .

I did not really notice the case if the command I was typing in, I will keep that in mind for future installs and updates.  The install worked great and I was able to update firefox :mrgreen: .

Thank You
LS.

---

### Post by Resurrection on 2006-05-09
When in doubt as to the name of a file or directory, you can type

```
ls
```
or
```
ls -l
```

to list the contents.

Its like the old "dir" command from DOS, except ls is better.

---

### Post by Kvark on 2006-05-09
And tab completion reduces the risk for spelling errors. Type as many letters as you think is needed to avoid confusion about which command or file name you are typing and then hit tab. In this case it would be to type "D" and then hit the tab key to get "Desktop". (if you don't get the complete name after hitting tab then the terminal failed to guess what you're typing, double tap tab to see all possibilities)

---

### Post by aysiu on 2006-05-09
Just a tip: When command-line instructions are given, highlight, copy, and paste. Retyping is more likely to lead to errors.

---

### Post by LipSkidr on 2006-05-09
Thank you for all the advice, will prob need lots of it.  I am not over whelmed,  yet!  But I will be reading alot.

---

### Post by Clay85 on 2006-05-09
Hmm my terminal doesn't like me. I haven't gotten it to do anything yet.

```
clay@clay-zimmerly:/home$ cd clay
clay@clay-zimmerly:~$ ls
Desktop  Downloads  Music  Ubuntu Desktop.jpg
clay@clay-zimmerly:~$ cd Downloads
clay@clay-zimmerly:~/Downloads$ ls
installnewfirefox.sh
clay@clay-zimmerly:~/Downloads$ chmod -x installnewfirefox.sh
clay@clay-zimmerly:~/Downloads$ installnewfirefox.sh
bash: installnewfirefox.sh: command not found
clay@clay-zimmerly:~/Downloads$ ./installnewfirefox.sh
bash: ./installnewfirefox.sh: Permission denied

```

I have the same problem when trying to switch my bookmarks.html file to the one that actually has my bookmarks on it from my USB drive.

---

### Post by aysiu on 2006-05-09
[QUOTE=Clay85]clay@clay-zimmerly:~/Downloads$ chmod -x installnewfirefox.sh[/QUOTE] You want to do chmod +x, not -x

---

### Post by Kvark on 2006-05-09
[QUOTE=Clay85]clay@clay-zimmerly:~/Downloads$ chmod -x installnewfirefox.sh[/QUOTE]
Minus removes permissions while plus adds them. So it should be +x there.

---

### Post by user1397 on 2006-05-09
you could , of course, do all permissions changes graphically.
you would have to right-click on the file, go to the permissions tab, and then all of the read and execute permissions, and check the owner part for write.

---

### Post by Clay85 on 2006-05-09
Hehe, let me see if that works for the update....

I tried that with my bookmarks.html and I can't. It's greyed out. Won't let me change permissions. Any advice for that?

---

### Post by Clay85 on 2006-05-09
Well it worked for the update.

---

### Post by Kvark on 2006-05-09
[QUOTE=Clay85]I tried that with my bookmarks.html and I can't. It's greyed out. Won't let me change permissions. Any advice for that?[/QUOTE]
Who owns that file? I bet it belongs to root because it came from a partition that is owned by root or something. To change ownership to yourself:
```
sudo chown clay bookmarks.html
```

---

### Post by Clay85 on 2006-05-09
Ahh!! /hug

I've been trying to figure that out all day. :) Thank you so much.

---

### Post by Clay85 on 2006-05-09
Well now I have permisison to overwrite the file, and overwrite the file I have. But firefox is not reading it. I still have the default bookmarks. When I open ect/mozilla-firefox/profile/bookmarks.html my current bookmarks are there, I think firefox isn't looking at the file for some reason.

 I'm going to restart and see if that works.

---

### Post by Kvark on 2006-05-10
[QUOTE=Clay85]Well now I have permisison to overwrite the file, and overwrite the file I have. But firefox is not reading it. I still have the default bookmarks. When I open ect/mozilla-firefox/profile/bookmarks.html my current bookmarks are there, I think firefox isn't looking at the file for some reason.

 I'm going to restart and see if that works.[/QUOTE]
Oh, you where going for the wrong file.

All your personal settings are in your home dir together with all your personal files. So normal users never have to go outside of their home dir. In fact normal users don't even have write permission to anything outside of their home dir.

For example my personal bookmarks are located at:
/home/kvark/.mozilla/firefox/8ekrswgn.default/bookmarks.html

Note that ".mozilla" starts with a dot. Files that starts with a dot are hidden. To see them you must do "ls -a" in the terminal, right click in an open/save dialog and choose "show hidden files" or press Ctrl+H in Nautilus.

The bookmark file you changed is outside of your home dir and everything out there is system files and system settings that only root should mess with, now we know why it belonged to root. My guess is that Firefox copies that file when it needs to give new users a bookmark file.


The difference between root and normal users may seem strange if you are the only one using the computer. It is good because the less time you spend as root the less risk there is that you accedentally mess up the whole system. And only programs that you use with sudo can mess up or take over the system if they would contain bugs or even trojans. Also if you give someone else access to your computer then don't give their account the right to use sudo to become root, that way they can only mess up their own home dir, the rest of your computer is safe from whatever they come up with.

---

### Post by Clay85 on 2006-05-10
Huh... That makes a great deal of sense. I don't think I'll be going back to WINXP except for my beloved games.

Thanks. :)

---

