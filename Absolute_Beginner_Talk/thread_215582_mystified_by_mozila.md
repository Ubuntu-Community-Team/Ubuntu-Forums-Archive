---
title: "mystified by mozila"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by lex1 on 2006-07-14
just installed mozilla-thunderbird-enigmail with aptitude.

I thought as well as being a mail client with gnupg it was a web browser as well?

am i incorrect.?

lex1

---

### Post by mostwanted on 2006-07-14
Yes. Firefox is the browser, Thunderbird is the email client. If you want both at the same time, take a look at Seamonkey.

---

### Post by Thorndeux on 2006-07-14
> **lex1 said:**
> just installed mozilla-thunderbird-enigmail with aptitude.

I thought as well as being a mail client with gnupg it was a web browser as well?

am i incorrect.?

lex1

Yes, you are. The package you installed (see here:[http://packages.debian.org/stable/mail/mozilla-thunderbird-enigmail]("http://packages.debian.org/stable/mail/mozilla-thunderbird-enigmail")) is a specific extension for Mozilla Thunderbird, which is a Mozilla-based mail client. The corresponding browser is Mozilla firefox.

---

### Post by lex1 on 2006-07-14
thanks for your post.

ok tried to uninsatll with aptitude mozilla-thunderbird-enigmail but it still remains reason for the first output below is because this was my 2nd attempt to remove

root@lex1# aptitude remove mozilla-thunderbird-enigmail
Reading package lists... Done
Building dependency tree... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages have been kept back:
  gdm gnupg language-pack-en libgtk2.0-0 libgtk2.0-bin libgtk2.0-common 
  libpango1.0-0 libpango1.0-common libsmbclient linux-386 linux-image-386 
  linux-restricted-modules-386 linux-restricted-modules-common login passwd 
  pcmcia-cs pmount ppp spamassassin wpasupplicant xserver-xorg-core 
  xserver-xorg-input-mouse 
0 packages upgraded, 0 newly installed, 0 to remove and 22 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
root@lex1:~# 


tried to remove enigmail on its own and got this:


root@lex1 aptitude remove enigmail
Reading package lists... Done
Building dependency tree... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find package "enigmail".  However, the following
packages contain "enigmail" in their name:
  enigmail-locale-ca enigmail-locale-de enigmail-locale-pt-pt 
  enigmail-locale-cs enigmail-locale-fi enigmail-locale-fr 
  enigmail-locale-ja enigmail-locale-hu enigmail-locale-it 
  enigmail-locale-nb enigmail-locale-nl enigmail-locale-pl 
  enigmail-locale-sk enigmail-locale-sl enigmail-locale-ru 
  enigmail-locale-sv enigmail-locale-es-es mozilla-thunderbird-enigmail 
  mozilla-enigmail enigmail-locale-pt-br 
The following packages have been kept back:
  gdm gnupg language-pack-en libgtk2.0-0 libgtk2.0-bin libgtk2.0-common 
  libpango1.0-0 libpango1.0-common libsmbclient linux-386 linux-image-386 
  linux-restricted-modules-386 linux-restricted-modules-common login passwd 
  pcmcia-cs pmount ppp spamassassin wpasupplicant xserver-xorg-core 
  xserver-xorg-input-mouse 
0 packages upgraded, 0 newly installed, 0 to remove and 22 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
root@xstation:~# xserver-xorg-core 
  xserver-xorg-input-mouse 
0 packages upgraded, 0 newly installed, 0 to remove and 22 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
root@xstation:~# xserver-xorg-core 
  xserver-xorg-input-mouse 
0 packages upgraded, 0 newly installed, 0 to remove and 22 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
root@lex1:~#

---

### Post by Thorndeux on 2006-07-14
I can't answer your question, I'm still a beginner myself, but WHY THE HECK ARE YOU MESSING AROUND AS ROOT???
If you decide to log in as root you should know exactly what you are doing.

---

### Post by lex1 on 2006-07-14
because you cannot install or remove progs if not in root its same as doing 
sudo aptitude remove or install

oupps maybe its not?

lex1

hey less of the shouting

---

### Post by Thorndeux on 2006-07-14
As I understand it sudo was desinged so you wouldn't have to login as root. I think it's certainly worth the effort to type sudo and your passwort from time to time. The point is that you minimize the time were you can mess with your system. With sudo you have only administrative permission for the time of the command.

---

### Post by lex1 on 2006-07-14
yes you are most certainly correct.
ok
so does anyone know how to solve my remove issue please?

lex1

---

