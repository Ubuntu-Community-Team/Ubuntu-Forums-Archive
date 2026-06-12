---
title: "Can't run anything"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by superbeef on 2006-10-26
Hey guys. Just got ubuntu on this computer I got off ebay :p . Didn't have an operating system or anything, and I heard this was good (and it is very nice)

But on to my problems.

Just about any time I try to run any form of application that hasn't been installed through the add/remove thing, it will not run. For one, the linux version of limewire. None of it runs, if I try to run any executable, whether it be in terminal or not, will not do anything. Also, I'm trying to run Xlink kai, and that does the exact same thing. There were a few others, but those are my main two concerns. Any help is much appreciated. Thanks.

---

### Post by kvonb on 2006-10-26
Are you trying to run it from a terminal?  If so, did you change it's permissions to "executable"?

Post here what you are trying to do, ie the command you are trying to run, and how you are doing it.

Maybe someone can help with a little more information.

Regards,

Kev.

---

### Post by superbeef on 2006-10-26
Okey, when I unzipped all my xlink kai stuff on my desktop, and it gave me two files: kaid and kaid.conf. First I tried running kaid by doubling clicking it, nothing happens. I did the same thing with kaid.conf, and it said it was an excecutable text file and what I should do with it, either run, run in terminal, or display it. Tried all of them, nothing happened (it did display, but that wasn't much help). So, I tried just using terminal to run it, using "exec /home/superbeef/Desktop/kaid-7.0.0.7-linux-x86/kaid" and "exec /home/superbeef/Desktop/kaid-7.0.0.7-linux-x86/kaid.conf", both of which made terminal close. The permissions are set to executable too.

---

### Post by kvonb on 2006-10-26
OK, just did a little research, what you need to do is install Automatix, go here:

[http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38#Installing_Automatix2_with_Apt](http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38#Installing_Automatix2_with_Apt)

Follow the instructions there, one completed you need to run Automatix and select "Frostwire" from the "File Sharing" category.

There is a lot of cool other stuff in Automatix too.

Regards,  Kev :)

---

### Post by superbeef on 2006-10-28
Thanks with the help with the frostwire thing.

It seems nothing I try to run is because didn't use the sudo thing. This seems to help in most situations, though I still can't get kai to work, lol. Different issue this time, though. I posted in a different thread about it, so i'll leave it there.

---

### Post by shookone on 2006-11-08
First put your kaid.conf file in /etc and your kaid into /sbin.

Then edit your kaid.conf file so that you may log in. Do not forget to port forward as you would in windows.

```
sudo nano /etc/kaid.conf
```

After you save the information edited from the command line run:

```
sudo kaid
```

Then connect with XBMC or any kaiui.

---

