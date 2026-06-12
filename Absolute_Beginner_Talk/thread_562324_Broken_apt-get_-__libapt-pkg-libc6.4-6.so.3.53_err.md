---
title: "Broken apt-get -  libapt-pkg-libc6.4-6.so.3.53 errors everywhere"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by NEUR0M4NCER on 2007-09-28
Hi all. Is there any way to get libapt-pkg-libc6.4-6.so.3.53 back onto my system? Nothing seems to work without it, Aptitude/Apt-Get included. Might it be on the LiveCD?


Hope someone can help, I could do without *another* fresh install.

Cheers

---

### Post by CaptainInsaneO on 2007-09-28
What's the error message you're receiving?

---

### Post by NEUR0M4NCER on 2007-09-28
I get:
```
sam@sam-linux:~$ sudo apt-get update
apt-get: error while loading shared libraries: libapt-pkg-libc6.4-6.so.3.53: cannot open shared object file: No such file or directory
```

and that's for pretty much anything that deals with packages, Synaptic included.

---

### Post by bapoumba on 2007-09-28
Have you tried:
```
sudo apt-get -f install
sudo dpkg --configure -a
```

---

### Post by CaptainInsaneO on 2007-09-28
I'd recommend the idea you had: try finding the library on your LiveCD and copy it over. This is a real problem because it affects your package handling, if it affected something else you could just apt-get the lib files. lol

I'll keep looking for a solution while you try that out. :)

---

### Post by NEUR0M4NCER on 2007-09-28
Yeah, tried that;
```
sam@sam-linux:~$ sudo apt-get -f install
apt-get: error while loading shared libraries: libapt-pkg-libc6.4-6.so.3.53: cannot open shared object file: No such file or directory
```

Anything to do with apt-get yields the same response. Aptitude also.

---

### Post by CaptainInsaneO on 2007-09-28
Go into /usr/lib and see if the lib file is even there at all. Maybe it just got renamed, if it's not there at all you should just be able to copy it from the LiveCD. :popcorn:

---

### Post by NEUR0M4NCER on 2007-09-28
Thanks Captain. I've tried searching the LiveCD for the file, with no luck. Another site suggested sudo apt-get install apt --fix missing, but again, if it involves apt, the error comes up. I imagine the file is contained in something else on the CD...

---

### Post by NEUR0M4NCER on 2007-09-28
The lib folder is there - is that what you mean? (sorry, still kinda new to Linux, although I can just about navigate in the terminal)

---

### Post by CaptainInsaneO on 2007-09-28
Have you tried looking in your lib directory on your hdd? Maybe the file got renamed somehow. Also, have you installed anything like Google Earth or Java lately? (Basically, anything that requires a license agreement). I've heard those can break packages.

Edit: If your lib directory is there, go into it and see if this file is there:

```
libapt-pkg-libc6.4-6.so.3.53
```

or something that looks close to it.

---

### Post by NEUR0M4NCER on 2007-09-28
You might be onto something there. The file is there, but it has a red cross over it - dies that mean it's disabled, and if so, can I re-enable it?

---

### Post by NEUR0M4NCER on 2007-09-28
The properties of the file lists it as file type: Link (broken) with the link target as /usr/lib/libapt-pkg-libc6.4-6.so.3.53.0   ...

---

### Post by CaptainInsaneO on 2007-09-28
Can you possibly post a screenshot so I can get a better idea of what you mean by red cross? I've never heard of that before and would like to see it. I can also help you more when I get home and can try to recreate your problem on my machine (I'm at work now, as usual :lolflag:) so we can get you fixed. I can also boot my LiveCD to search for that file so I can guide you to it.

I believe everything is fixable in Linux, and my ultimate goal is to keep you from having to re-install your OS. I'm sure this is a simple fix, we're just missing something.

I won't leave you hanging, don't worry. :guitar:

---

### Post by NEUR0M4NCER on 2007-09-28
Thank-you so much! Screenshot should be attached - if you look over to the right of the screen in the file browser window you'll see what I mean about the red x.

---

### Post by CaptainInsaneO on 2007-09-28
Great! Now I see clearly now (the rain is gone) ahem. Ok. :lolflag:

The file that it's linking to (libapt-pkg-libc6.4-6.so.3.53.0) is missing. I'll search for a solution when I get home tonight, I'll keep you updated.

---

### Post by NEUR0M4NCER on 2007-09-28
Wonderful. Thank-you for all of your help Captain!

---

### Post by NEUR0M4NCER on 2007-09-28
So I managed to get a copy of the required file on IRC... extracted, moved into /usr/lib but it doesn't solve anything. I'm stumped.

---

### Post by CaptainInsaneO on 2007-09-28
We both use Ubuntu Ultimate (I'm assuming, from your screenshot) so try out my lib file and see if it works for you. Just copy the file in this archive straight into your /usr/lib folder.

---

### Post by NEUR0M4NCER on 2007-09-29
Thanks for the upload. I just can't seem to get the d*mn file into /usr/lib. There's a folder in there of the same name, that stops me from copying it across... how do I go about that?

---

### Post by bapoumba on 2007-09-29
I do not have the same version number, but could you verify the symbolic link on the lib is still there ?
```
:/usr/lib $ ls -la libapt-pkg-libc6.6-6.so.4.5*
lrwxrwxrwx 1 root root     29 2007-09-23 23:40 libapt-pkg-libc6.6-6.so.4.5 -> libapt-pkg-libc6.6-6.so.4.5.0
-rw-r--r-- 1 root root 842812 2007-09-22 23:28 libapt-pkg-libc6.6-6.so.4.5.0
```

---

### Post by NEUR0M4NCER on 2007-09-29
You mean on the icon itself? No, the link part is not there.

---

### Post by CaptainInsaneO on 2007-09-29
Your user account doesn't have the permission level required to copy files into the lib directory, you need to get temporary root permission in a nautilus window. Do this in terminal:

```
gksu nautilus
```

Be VERY careful while you're in this window, there's a lot of potential to mess your system up beyond repair.

Once the nautilus window opens, navigate to your /usr/lib directory and copy that file over.

---

### Post by NEUR0M4NCER on 2007-10-01
I'd love to be able to tell you I fixed it all, but I can't. Fresh install solved the problems, luckily Ubuntu install only takes 30 mins unlike XP's 3 hour drama.

Thanks for all of your help anyway Captain. People like yourself are the main reason people like *my*self make the switch from Windows to Linux. Cheers dude.

---

### Post by CaptainInsaneO on 2007-10-01
Well you DID fix it, in a way. Sometimes (and I hate to admit this) a re-install is the easiest way to go.

Sorry I couldn't help more, I'd really like to know what happened to your apt.:confused:

---

### Post by nardis_Miles1 on 2007-11-10
So I stumbled on this thread because I had the same problem. Thank you for posting the bzipped tar-file. Using a lowly command line and sudo, I was able to unpack it. I think that NEUROM4NCER's problem is that the file, as unpacked, is libapt-pkg-libc6.4-6.so.3.53.0 .

ln -s libapt-pkg-libc6.4-6.so.3.53.0 libapt-pkg-libc6.4-6.so.3.53

made that particular problem go away... not that there aren't many others in this install.

---

