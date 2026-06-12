---
title: "how to make a bootable CD for Ubuntu"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by black_ice on 2007-01-29
[B] hello all ..., 

i copied a CD contents of Ubuntu 6.10 and i want to make it in iso format to make it bootable and install it !!!!!!!!!!!!!!!!!![/B]

---

### Post by dbbolton on 2007-01-29
use gnomebaker to burn a data cd, and put all the contents into the gnomebaker project. when it's time to burn it, choose "burn to file" and it will write an iso.

note, thousands of exclamation points aren't necessary.

---

### Post by black_ice on 2007-01-29
thanx Mr. : dbbolton

am now on the Windows Xp and i want to make that CD to work on Ubuntu So can I use Nero ?? and choose Burn to File ? ;

---

### Post by CCBalla10 on 2007-01-29
go to google and search for a very small program called isorecorder
i believe it is to version 2 now...worked great for me, and burned very fast!

---

### Post by black_ice on 2007-01-29
i used iso recorder and i get this error operation failed code : 8004021c, Reason the disc cannot hold any more data !!!

---

### Post by CCBalla10 on 2007-01-29
are you using an 80 min cd?  also i think ISO recorder has an option to choose the size of your cd/dvd you are using
Ubuntu just barely fits on an 80 min cd

---

### Post by black_ice on 2007-01-29
than CCBalla for your great support 

but i setup the iso recorder in the windows and i cannot simply find the program properties to adjust it to 80 min am using program by clicking on the dir  want it to be iso and the job done ! cAN U TELL ME WHERE I CAN FIND THE PROGRAM PROPERTIES !!! 

THANX

---

### Post by The Tronyx on 2007-01-29
From nero choose the option to burn a data CD and **burn the .iso file as an image.**

---

### Post by black_ice on 2007-01-29
so i can use nero and burn it as data cd and it will be bootable ?

---

### Post by IronMac on 2007-01-29
The following is for Ultimate Boot CD but the process should be the same:

[http://www.ultimatebootcd.com/nero6.html](http://www.ultimatebootcd.com/nero6.html)

---

### Post by black_ice on 2007-01-29
** thanx for ur help but all i need is HOW TO MAKE AN ISO FILE FROM THE DIRECTORY OF THE CD THAT I HAVE COPIED IT :(**

---

### Post by logos34 on 2007-01-29
In Nero choose burn an **image**, not a data cd.

---

### Post by xmastree on 2007-01-29
See this to make your bootable CD with nero/Win XP:

[http://www.xmastree.34sp.com/ubuntu/burn](http://www.xmastree.34sp.com/ubuntu/burn)

Please rephrase your last question so that it makes sense...

Oh, and **STOP SHOUTING**

---

### Post by black_ice on 2007-01-29
ok thanx for every one posted in the subject .... 

all i need is >>>

i have copied the contents of the cd for ubuntu 6.10 and it was a directory   named with "Ubuntu 6.10 i386 (G)" all i need is to convert this directory to .iso format ho can i make this....... after that i will able to burn it with any iso burner

---

### Post by xmastree on 2007-01-29
So, you started with an ubuntu CD and copied the contents?

You're stuck. :-(

Without the boot sector (which is contained in the ISO) you won't be able to make it boot as intended.

If you still have the CD you copied from, then you can make the ISO from that with nero.

---

### Post by black_ice on 2007-01-29
so u think itis impossible to take this directory and make it in iso format >>? 

do u think itis better to just redownload it ?

---

### Post by CCBalla10 on 2007-01-29
> **black_ice said:**
> so u think itis impossible to take this directory and make it in iso format >>? 

do u think itis better to just redownload it ?

Yes...better to re-download

---

### Post by sonhadorpr on 2007-09-10
My dear Ubunteros!
I am a newbie in Ubuntu, but gaining more experience everyday. I have a project at the U. helping a professor run a rather large program, on his multi-processor server. He had an idea that if we could make a Live Bootable CD, that runs a certain program (or 2 or 3)on any PC, without installing the OS, just running the program, so that they could connect to this server, and run the big program, it would help speed things up.
Anybody know how to make a Live bootable CD.
Does anybody understand what I'm trying to do?...Can it be done?

I need to make this bootable CD, taking many programs out(like the Open Office, games, etc...in order for it to fit a 700MB disk) and add NFS and mount in local directory on server machine, add NIS to use accts info and login on every machine, add ssh and run remote commands with rsh, add MPI, Gromacs, and run OS from the server.

Anybody knows?
Thank you for your help.
So mainly, I need to know how to make an ISO file.

---

