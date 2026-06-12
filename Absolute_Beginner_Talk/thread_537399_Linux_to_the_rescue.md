---
title: "Linux to the rescue"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by sw1995 on 2007-08-28
Hello!

I have a few questions: I have been using Ubuntu happily for a few months and feel as though I am pretty confident with the operating system. I am now faced with my first, "how can I save my roommates' computer with Linux" dilemma.

He runs Windows and it refuses to boot up (well, it gets to the desktop and the entire PC shuts down and starts all over). The computer is a mess to begin with and I suspect ridden with viruses, etc.

Long story short, I have  a number of live cds around (although I'd love to stick with Ubuntu) so I was wondering:

How do I use an Ubuntu live cd to boot onto his computer and then get his photos, documents, etc off so that I can subsequently install Ubuntu as the main OS (I know how to install Ubuntu, I'm just wondering how do I use it to access the information on the hard drive)?

As always, any help would be appreciated!

-S

---

### Post by Niklas Schröder on 2007-08-28
you need to mount a hard drive to read it

plunk one of the live cd's in his pc, boot it up, do this...

```

cd /mnt

```
```

sudo mkdir windrive

```
```

sudo mount -t ntfs /dev/sda2 /mnt/windrive -o &#8220;umask=022&#8243;

```
```

ls windrive

```

backup the data (preferably to cd), then do...

```

gksudo gparted

```

delete the windows partition, and then open the installer and choose "install in largest free contiguous space" (or similar).

***Explanations:***

cd = change directory

sudo = we need to be root

mkdir = make a directory

```
sudo mount -t ntfs /dev/sda2 /mnt/windrive -o &#8220;umask=022&#8243;
``` 
is the code to mount the drive the right way if you would like to know more on that type "man mount"

```
ls windrive
``` 
will list everything in that drive

---

### Post by the.phantom on 2007-08-28
might boot into "safe mode" on windows
1, did it boot ok and not crash?
2. from there you could run the anti-virus 
3. you can have it list the boot sequence and see where it crashes

---

### Post by Niklas Schröder on 2007-08-28
or, if he doesn't care about losing settings and the like, and if he owns a dell, he could use the symantec pc restore... 

> 
[http://support.dell.com/support/topics/global.aspx/support/dsn/en/document?c=us&l=en&s=gen&dn=1090151](http://support.dell.com/support/topics/global.aspx/support/dsn/en/document?c=us&l=en&s=gen&dn=1090151)


to re-install after saving his data through ubuntu.  that's what i did when my system died on me.

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-08-28
yes so thats what you need to do if you would like to know what that means 
you need to mount a hard drive to read it , thats what were going to do
to mount a hard drive you need a folder in the file system that you will acesses the hard drive through so make that first and i should be in a good spot like the /mnt dirctory
(i dont know y but he did it and it looks good :)  )

then finaly mount the dirve so that explanes the other post a little bit
cd is change diretory 
sudo is there becuses we need to be root
mkdir is make a directory
sudo mount -t ntfs /dev/sda2 /mnt/windrive -o “umask=022&#8243; is the code to mount the drive the right way if you would like to know more on that tyep "man mount"
ls windrive will list everything in that drive

---

### Post by HermanAB on 2007-08-28
You can also boot his PC with BartPE (a Windows XP based Live CD) then mount a network or USB drive and do a backup that way.

Cheers,

Herman

---

### Post by Niklas Schröder on 2007-08-28
thanks for the explanations <<joe>>.  :)  mind if i add them to my post?

---

### Post by freebeer on 2007-08-28
I had a similar experience... booted the 7.04 LiveCD and it auto-detected the domain and the NTFS file system.  I just copied the relevant documents across the network and I was done.  Couldn't have been easier!

---

### Post by hyper_ch on 2007-08-29
You can also reinstall windows in a nother directory than c:\windows e.g. c:.\winnt and just don't have the harddisk formatted...

Then load some cd-burning program or network the computer to backup the stuff before wiping everything.

---

### Post by sw1995 on 2007-08-29
I finally got the Ubuntu live cd to load (it just happened, honestly, this computer is a disaster; I was turning it on and off and finally the miraculous Ubuntu screen popped up). I have reinstalled and installed Ubuntu a number of times, however (and I have always ONLY installed Ubuntu, never dual booted),THIS TIME the desktop now has two icons that say "disk" (the two icons themselves says "SD") What the heck is this? Some weird Windows stuff I imagine. Nonetheless, I am totally running the Ubuntu live cd, have the internet going, so I would like to know, what is the next step? The computer is a total mess. We're not trying to save it--from where we are can we recover his old information or should we just go ahead and install Ubutnu (which is what I want to do, I had a hard enough time booting into the live cd...this system is a mess). Can we get any of the photos and etc. off of it or should I just install Ubuntu over the drive? We would rather not make this too complicated. Sorry.

Thank you, you mad men Linux heroes!

-S

---

### Post by hugmenot on 2007-08-29
Just go into "Places" &#8594; "Computer" and open the drive icons there. They should be mounted automatically. Then attach a USB storage device (Hard disk, large USB stick, iPod) and copy everthing he needs onto that (should automount as well).

Then start the install and wipe the whole thing. Verify that you got everything off first.

---

### Post by sw1995 on 2007-08-29
> **hugmenot said:**
> Just go into "Places" &#8594; "Computer" and open the drive icons there. They should be mounted automatically. Then attach a USB storage device (Hard disk, large USB stick, iPod) and copy everthing he needs onto that (should automount as well).

Then start the install and wipe the whole thing. Verify that you got everything off first.

Thank you! I just realized that the two "disk" icons on the desktop were his files...I just was afraid to click on them because of the whole Windows thing (good lord, I haven't used Windows in so long, it has been a funny experience dealing with such problems!!!!!!!! I am so comfortable with what I have learned with Linux/Ubuntu that my friend had a problem with Windows and I got all choked up! YOU MEAN YOU ARE HAVING A PROBLEM???...DUDE, it's been a long time...I'm not even sure HOW to fix a Windows problem any more...I'll go to Ubuntuforums.org!!!!!!!!!) Long story short, this community is insane. Thanx.

This is "S" signing out, getting ready to turn an old busted Windows computer into a bad **** Ubuntu machine for my roommate! Ciao!

Respect,

-S

---

### Post by Niklas Schröder on 2007-08-31
if he doesn't care about the data on there, then just wipe it.  it's not worth it.  you'd have to run virus scans on the files when you got them off if you ever wanted to interface with another windoze computer again anyway.  personally, unless i had an extensive music collection, school work, or family photos on there, i wouldn't even bother.

---

