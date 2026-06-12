---
title: "DVD Backup"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by RDUBBALO on 2007-01-29
Does anyone know of software I can get for Ubuntu to backup my dvd's something similar to clone dvd. Does the k9copy work for that or any other program in the ubuntu program list?

---

### Post by RDUBBALO on 2007-01-29
maybe graveman?

---

### Post by RDUBBALO on 2007-01-29
does this all have to be done through the command line i know how to rip them but how do i burn a disk. ISO file?

---

### Post by RDUBBALO on 2007-01-29
How about this does anyone know how to install or even download the libdvdcss2 for encrypted dvds?

---

### Post by yabbadabbadont on 2007-01-29
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

That should answer most of your questions.  Post back with any that remain.

---

### Post by RDUBBALO on 2007-01-29
I read that already Im not sure what i need to download or install. its alittle confusing.

---

### Post by halitech on 2007-01-29
try using k3b to make an ISO and then to burn that iso, thats what I've used and it's worked pretty good.

---

### Post by RDUBBALO on 2007-01-29
What is that and how do i get it? I got the k9copy and it works great except on newer dvds that have encryption it says to dl and instal the libdvdcs2 and I cant figure that part out I dl it and where do i install it or how. IDK

---

### Post by halitech on 2007-01-29
easiest way to get that would be with automatix2 ( [http://www.getautomatix.com]("http://www.getautomatix.com") ) and for k3b, it's in the repos in synaptic (System - Administration - Synaptic)

---

### Post by ardchoille42 on 2007-01-30
> **RDUBBALO said:**
> What is that and how do i get it? I got the k9copy and it works great except on newer dvds that have encryption it says to dl and instal the libdvdcs2 and I cant figure that part out I dl it and where do i install it or how. IDK

I installed libdvdcss2 with:
```

sudo aptitude install libdvdread3
sudo sh /usr/share/doc/libdvdread3/examples/install-css.sh

```
If you can't run that script, fetch libdvdcss2 from [here]("http://www.dtek.chalmers.se/groups/dvd/deb/").

There is an awesome app that will backup dvd movies, if that's what you're trying to do, it's called xdvdshrink and is available [here]("http://dvdshrink.sourceforge.net/"). I have used xdvdshrink to make copies of all the DVD's I purchased and it does quite a good job. It shrinks a dual-layer (DVD9) DVD movie down to fit on a single-layer (DVD5) disk. You'll need to install some dependencies to use xdvdshrink but the xdvdshrink installer checks for them and lets you know what you need to install.

I am running xdvdshrink on Dapper and it runs fine.

---

### Post by Brandel Valico on 2007-01-30
Okay here is what I do.

I open k9copy set it to autoburn the dvd in k3b.

Doing this will take the iso k9 makes and open k3b up and have it all set so you just have to press the burn button after putting the blank dvd in. (That assumes you only have your burner to read and write with of course)

I use this method becuase k9copy will also shrink the DVD down to fit onto a standard DVD similar to dvdshrink.

There are other methods to do this. but for overall control of the process like taking out the extra audio and subtitles that I don't need. it's about the best GUI method I have found to do this.

---

### Post by Zzl1xndd on 2007-01-30
I use DVDstyler for burning my DVD's dont know if it will suit your needs

---

### Post by RDUBBALO on 2007-01-30
> **Brandel Valico said:**
> Okay here is what I do.

I open k9copy set it to autoburn the dvd in k3b.

Doing this will take the iso k9 makes and open k3b up and have it all set so you just have to press the burn button after putting the blank dvd in. (That assumes you only have your burner to read and write with of course)

I use this method becuase k9copy will also shrink the DVD down to fit onto a standard DVD similar to dvdshrink.

There are other methods to do this. but for overall control of the process like taking out the extra audio and subtitles that I don't need. it's about the best GUI method I have found to do this.

yeah but it wont let me do the authoring because it cannot read the disc since it is encrypted. I dont know how to get past that. i know it works cause i already burned a few dvds with k9copy.

---

### Post by RDUBBALO on 2007-01-30
alright i dl dvdshrink what do i do with it now I dont know how to install this thing.

---

### Post by ardchoille42 on 2007-01-30
> **RDUBBALO said:**
> alright i dl dvdshrink what do i do with it now I dont know how to install this thing.

```

tar xzf /path/to/dvdshrink-2.6.1-8mdk.tar.gz
cd /path/to/dvdshrink
sudo sh install.sh

```
That install script will check your system and report what it finds. It's self-explanatory and you may need to install some deps and then re-run the installer.

---

### Post by RDUBBALO on 2007-01-30
> **ardchoille42 said:**
> ```

tar xzf /path/to/dvdshrink-2.6.1-8mdk.tar.gz
cd /path/to/dvdshrink
sudo sh install.sh

```
That install script will check your system and report what it finds. It's self-explanatory and you may need to install some deps and then re-run the installer.

that didnt work I put this in the terminal? I installed it but it says i have other things missing. IDK this is turning out to be difficult. How can I just get the libdvdcss2 installed

---

### Post by ardchoille42 on 2007-01-30
> **RDUBBALO said:**
> that didnt work I put this in the terminal? I installed it but it says i have other things missing. IDK this is turning out to be difficult.
I told you there would be deps to install. The xdvdshrink install script will tell you what you need and then you can install them with Synaptic. Once that's done, you can re-run the xdvdshrink install script.


> How can I just get the libdvdcss2 installed
You need to install libdvdread3 and then open a terminal and do:
```

sudo sh /usr/share/doc/libdvdread3/examples/install-css.sh

```
That will install libdvdcss2 for you.

---

### Post by RDUBBALO on 2007-01-30
it says it cant open it that file you told me there. I appreciate your helping me out.

---

### Post by ardchoille42 on 2007-01-30
> **RDUBBALO said:**
> it says it cant open it that file you told me there. I appreciate your helping me out.

Did you install libdvdread3 ?

---

### Post by RDUBBALO on 2007-01-30
i guess i used. sudo aptitude install libdvdread3

---

### Post by RDUBBALO on 2007-01-30
ok i installed all those things i needed now i reinstalled dvdshrink now how do i run it. and it also says it will need to be reconfigured next time i use it.

---

### Post by ardchoille42 on 2007-01-30
Open a terminal and run:

xdvdshrink

If you haven't yet installed libdvdcss2, you still need to do that:

sudo sh /usr/share/doc/libdvdread3/examples/install-css.sh

---

### Post by RDUBBALO on 2007-01-30
command not found

---

### Post by RDUBBALO on 2007-01-30
> **ardchoille42 said:**
> Open a terminal and run:

xdvdshrink

If you haven't yet installed libdvdcss2, you still need to do that:

sudo sh /usr/share/doc/libdvdread3/examples/install-css.sh

-desktop:~$ sudo sh /usr/share/doc/libdvdread3/examples/install-css.sh
sh: Can't open /usr/share/doc/libdvdread3/examples/install-css.sh

---

### Post by RDUBBALO on 2007-01-30
can i just use automatix someone said to use that and i see it there.

---

### Post by RDUBBALO on 2007-01-30
how do i uninstall dvdshrink i want it out.

---

### Post by Brandel Valico on 2007-01-30
You need to install libdvdcss2 to get around the encryption issue I believe.

I have made a great many backups of my store bought DVDs encrypted and not with k9copy and k3b.

Run the below in your terminal and you should be all set.
> sudo apt-get install libdvdcss

---

### Post by Brandel Valico on 2007-01-30
I believe > sudo apt-get remove xdvdshrink

Should remove dvdshrink.

But I'm also fairly new to linux myself so if at all possiable do a search and ensure I'm right before you do so.

As for Automatix it's probably the easiest way to install all the files you will want for day to day users who just want their media to work.

---

### Post by RDUBBALO on 2007-01-30
> **Brandel Valico said:**
> I believe 

Should remove dvdshrink.

But I'm also fairly new to linux myself so if at all possiable do a search and ensure I'm right before you do so.

As for Automatix it's probably the easiest way to install all the files you will want for day to day users who just want their media to work.

What is this automatix saying that I have to pay money to people for using the libdvdcss Where do you pay money to? Oh and that dvdshrink remove didnt work cannot find. Thanks for all the help. I got it working now from Automatix. K9copy works perfectly.

---

### Post by Brandel Valico on 2007-01-30
Not sure about the paying money for use of libdvdcss. Never heard of having to do so.

Either way glad you got it working. Sorry I wasn't more help with the xdvdshrink removal.

Still if nothing else you could always go remove it in Synaptic.

---

### Post by RDUBBALO on 2007-01-30
nah thanks for everything you got me alot of help. thanks again.

---

