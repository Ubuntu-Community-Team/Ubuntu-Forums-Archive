---
title: "stuck installing Realplayer/Helix"
date: 2007-06-06
forum: Apple PPC Users
---

### Post by thedarky on 2007-06-06
Howdy, 

I'm new to linux and ubuntu, unfamiliar with command line syntax, and I can't get past copy/paste simple instructions to get this Realplayer plugin installed.

I need Realplayer so that I can listen to the BBC, PRN and a couple of other public radio networks, so alternative general  media players that are in the apt and syn repositories just don't fit this bill., much as I'd like to go the trouble-free way.

I'm following the official documentation here:
[https://wiki.ubuntu.com/PowerPCFAQ#head-4c512dc1fe442052d2bb368afeb4f8add9f83d71](https://wiki.ubuntu.com/PowerPCFAQ#head-4c512dc1fe442052d2bb368afeb4f8add9f83d71)

I have the binary file on the desktop, and the chmod command produces the following output

```
chmod +x realplay-10.0.4.750-linux-2.2-libc6-gcc32-powerpc.bin
chmod: cannot access `realplay-10.0.4.750-linux-2.2-libc6-gcc32-powerpc.bin': No such file or directory
```
same for the command with sudo in front.

Looking at the 'properties' tab in the desktop GUI,  I have enabled executable permission - but the 'open with' tab reports not knowing what to open the file with - which I guess is confirmation that it hasn't been made a recognisable file yet.

Output of the ls command
```
-rwxr-xr-x 1 me me  5114227 2007-06-06 14:48 realplay-10.0.4.750-linux-2.2-libc6-gcc32-powerpc.bin
```
with the file name highlighted in green

What steps should I take to troubleshoot this inability of my system to get this installation going?

thanks in advance for any help.
I'm working away from the puter, so could be slow in responding.  This isn't meant to imply that I am not trying very hard to get this problem worked out.

---

### Post by mainalisuyog on 2007-06-06
Just try running the following command in a terminal from the directory where u have saved the file.:

 ./realplay-10.0.4.750-linux-2.2-libc6-gcc32-powerpc.bin 

 If it doesn't work, i think u better install automatix and install realplayer through automatix. That's how I did it.

---

### Post by avtolle on 2007-06-06
You may have already done this and I missed it, but as you downloaded to the desktop, the first thing to do is to change your directory to the desktop, i.e.,at the terminal, the first command is "cd Desktop" (without the quotes, of course). Then run the commands you ran, and see what happens. BTW, as Linux is case sensitive, the capital D in Desktop is needed.

---

### Post by thedarky on 2007-06-06
> **avtolle said:**
> You may have already done this and I missed it, but as you downloaded to the desktop, the first thing to do is to change your directory to the desktop, i.e.,at the terminal, the first command is "cd Desktop" (without the quotes, of course). Then run the commands you ran, and see what happens. BTW, as Linux is case sensitive, the capital D in Desktop is needed.

Bingo, lightbulb is on - thanks avtolle.

Unfortunately, when running the installer (now recognised as a binary ppc file) it seems that there's a new hurdle to jump

> ./realplay-10.0.4.750-linux-2.2-libc6-gcc32-powerpc.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

I shall call this post resolved and go searching again.  There's a little voice telling me that maybe reverting to the realplayer 8 that's in the repository might be worth trying.  All I need is streaming radio - and that codec hasn't changed in years.

thanks again.

---

### Post by stmiller on 2007-06-06
```
$ sudo apt-get install libstdc++5 libstdc++5-3.3-dev

```

---

### Post by thedarky on 2007-06-07
Thanks so much stmiller :-)

I'd given up hope and was resigned to leaving the problem a while longer, but luckily saw your reply.

I can report to you that that bundle has enabled the installation and I have a fully functioning RealPlayer up and running.
Almost too scared to quit Feisty in case it disappears ;-)

thanks again.

---

