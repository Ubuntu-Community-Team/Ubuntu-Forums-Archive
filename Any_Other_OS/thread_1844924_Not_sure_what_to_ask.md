---
title: "Not sure what to ask?"
date: 2011-09-16
forum: Any Other OS
---

### Post by reaply on 2011-09-16
Basicly I asked this at the windows7 forum and got banned and I don't know what to do.

> Hey sevenforums, it's good to see you again (I wish it was under better circumstances.)

Ok so straight to the point, I installed windows 8 just for the fun of  it and I left it installing while I went to school. I come home from  school excited to try the new OS (and the new league of legends patch)  and I browse through windows 8 and I don't like what I see (when I got  home it was already logged in and everything) and I restart my computer  thinking it was portioned. It turns out it had over written windows 7.  So as my first response I download a torrent of windows 7. (I own  windows 7 but my computer that I bought it came with a key code on the  side of it and not a disc) and I don't have any discs so I extract the  iso and install from the setup. Time goes forward more and it installs  blah blah and I restart my computer and I let it install and everything  but it got stuck at wpeditini and i left it there for two hours and it  stayed there. So I went back into windows 8 and installed ubuntu for  backup reasons (it's what I am using right now.) And so I go for a  different torrent of windows 7 and it installs great this time but it  doesn't detect my enthernet card. It can detect my wireless card but not  my enthernet cable. So currently I can only access the web from ubuntu.  Any help here? Also, when I installed windows 8 it made my res not  work. Like it will say that I am using 1920x1080 but my screen is  covered by blackness and I just get a small box of a screen to see.Now I do own windows 7, but I only have a key (which was the only thing given to me with my pc.) This is besides the point. What I am here to ask is how can I transfer the windows file from ubuntu to windows. I am sure my ubuntu is corrupt since anytime I try to download something it says I need to insert a cd. And my cd drive won't open in ubuntu. Is there a way to drag the file to the windows files from ubuntu?

---

### Post by knutschr on 2011-09-16
I dont understand what you ask for, but I dont think your Ubuntu is corrupt. Open Synaptic, go to the Settings, Repositories section and remove the tick next to the CD-ROM option in the lower section of the "Ubuntu Software" tab.
Then it wont ask for cd-rom when you will install.

---

### Post by reaply on 2011-09-16
Hoi (I speak little Norwegian :p) Thank you for the reply!

So I cannot get the drivers for my souncard for windows since I cannot connect to the internet. I downloaded the driver software on ubuntu how can I transfer the file from ubuntu to windows? When i'm on ubuntu my cd drive does not open for some reason. Is there a way for me to find my windows folder from ubuntu and all I have to do is drag and drop?

---

### Post by -kg- on 2011-09-16
Yes.  Open your file browser (which version of Ubuntu are you running?  I don't know whether 11.04 still uses Nautilus, since I'm running Kubuntu right now) and go to "Computer."  You should see your Windows partition/drive there.

You'll need to double click on it to mount it.  Then press "F3", which will split the pane.  In one pane, navigate to the files on your Ubuntu drive, and on the other navigate to where you want to put those files.  Then it's just a matter of dragging the files from one pane to the other.

---

### Post by decrepit on 2011-09-16
Yep there is, firstly you have to identify the windows partition, then mount it.

```
sudo fdisk -l
```
should tell you the name of the windows partition.

To mount a partition you need a directory to mount it in.
So create a directory somewhere convenient, (I usually make a windows directory like this /mnt/windows)

Then 
```
sudo mount /dev/(windows partition) /mnt/windows
```

Problem is this method only gives root access so you'll need to start nautilus with root privileges
```
gksudo nautilus
```.

Note it's a security risk running nautilus like this so exit as soon as possible.
There are better ways of doing this, (giving direct access to windows) but I'm short of time at the moment and can't remember exactly how to do it

---

### Post by reaply on 2011-09-16
Ok this is the computer folder. I am not sure which one has the windows files?

[IMG]http://i53.tinypic.com/10yqp3r.png

This is the HD

[IMG]http://i51.tinypic.com/2imaur9.png

And this is the File System

[IMG]http://i52.tinypic.com/2agl1rn.png

Which one would I go to?

---

### Post by reaply on 2011-09-16
Sorry for this, but bump.

---

### Post by PhilGil on 2011-09-16
That looks like a WUBI install to me. I think you'll find your windows folders in File System --> Host

---

### Post by reaply on 2011-09-16
That takes me to my ubuntu files and not windows.

---

### Post by IWantFroyo on 2011-09-16
I don't know how you'll do the file sharing thing, but I can help with one thing.

Downloading a torrent is illegal. Microsoft hosts an official version of Windows 7 free of cost, that you have to activate to use.

---

### Post by reaply on 2011-09-16
It's not illegal if you have a key for it (I would venture to guess) my pc came with a key that is on a sticker on my computer and not with a disc. They preinstalled windows on it.

---

### Post by IWantFroyo on 2011-09-16
I know that. It's just Microsoft doesn't want you installing a rigged version of Windows, and then blaming them for it.

Edit- My point here, is that it's easy to make an infected Windows installation file. Don't be fooled. Use official stuff.

---

### Post by reaply on 2011-09-16
I cannot even find a download for windows on their website.

Also if this can be asked, when I downloaded windows 8 it wouldn't let me do 1920x1080 on my monitor so I have a black box that is surrounding what I can see (it's hard to describe) if anyone can understand what I mean and know how to fix it.

---

### Post by PhilGil on 2011-09-16
There are uncracked versions of Windows available on torrent sites, too. The original poster may be assuming a bit more risk downloading Win 7 from a torrent site, but I don't believe it's illegal.

Perhaps you'd be willing to point the OP to the site where Microsoft provides Win 7 for legal download.

---

### Post by IWantFroyo on 2011-09-16
I'll report the thread to a mod so that they can move this to Other OS/Distro Talk.

As for Windows, many of us haven't used it in quite a while, and the ones who do use Windows 7, not 8.

We just might not be able to help you.

Also, shouldn't there be some monitor settings in some control panel? I'm sorry, but that's all I remember.

---

### Post by GWBouge on 2011-09-16
Here's one:

[http://www.mydigitallife.info/download-windows-7-iso-official-32-bit-and-64-bit-direct-download-links/]("http://www.mydigitallife.info/download-windows-7-iso-official-32-bit-and-64-bit-direct-download-links/")

---

### Post by reaply on 2011-09-16
That would be nice. But I am not sure how I will even get windows 7 to install from ubuntu considering I can't even open my cd rom drive.

---

### Post by IWantFroyo on 2011-09-16
> **PhilGil said:**
> There are uncracked versions of Windows available on torrent sites, too. The original poster may be assuming a bit more risk downloading Win 7 from a torrent site, but I don't believe it's illegal.

Perhaps you'd be willing to point the OP to the site where Microsoft provides Win 7 for legal download.

Well, maybe not illegal by US law, but definitely frowned upon by Microsoft. I've heard about lots of people who got infected from what appeared to be official downloads on torrent sites, and many end up blaming MS.

As for where the download is, I really don't know. I read about it on a tech site a while back, but I can't remember the site or the link.
If you delve a bit into the Windows purchase web page, you might be able to find something in the small print. No guarantees, though.

---

### Post by IWantFroyo on 2011-09-16
> **reaply said:**
> That would be nice. But I am not sure how I will even get windows 7 to install from ubuntu considering I can't even open my cd rom drive.

If a friend has a removable optical drive, you could use that. Also, I hear you can install the Windows installation stuff onto a USB. You could probably do that on a friend's computer.

---

### Post by reaply on 2011-09-16
Does anyone know if windows setup will work with wine?

Also I have the fullest res on 1920x1080 and I get black areas around what I can actually see. It seems if it isn't 16:10 it will have a black box around it.

Also 2: This is still about ubuntu though, I just need a way to transfer files from ubuntu to windows.

---

### Post by GWBouge on 2011-09-16
Note sure what's going on with the filesystem, so can't really advise on where to move the files, but might help if you post the output of a command mentioned earlier:

```
sudo fdisk -l
```

As for the black areas, what graphics card are you using?  You might have to go into the nVidia/ATI Control Panel/Catalyst and slide up GPU Scaling until it takes up the entire monitor.  nVidia seems to always default to a full monitor (in my experience), but I've seen Catalyst default to like 90% of the screen area (which I think actually displays as 100%, and I had to slide up to 115% ... been a little while, though).  Edit:  That is, if you ever got to install the video drivers ...

---

### Post by reaply on 2011-09-16
Hey, I can see everything again! I got windows to install from the new windows that was suggested but I still don't have any enthernet drivers it says darn it :/.

---

### Post by Synoc on 2011-09-16
first off, the black lines... are they where your mouse point stops? if not stretch the background, if so, you might need to update the video drivers, without Ethernet, it's not possible for Windows Update to search the MS website for drivers. if you can use your ubuntu to download both ethernet drivers for your PC and video drivers, you can move them to the windows directory via nautilus. I recommend creating a folder called "drivers" for this. then just run the install. that SHOULD solve your problems. 

Second MS does not have a place to DL their OS that i know of. they have a microsoft technet site for members of technet so that techs can DL them, use them, break them, fix them and use them privately so they can use that knowledge to apply Windows networks and fix them. the subscription is not cheap.

I hope this information is helpful. please do not hesitate to respond to us if everything I just said was unhelpful. I am woefully still a Windozer, not by choice.

---

### Post by reaply on 2011-09-16
Awesome, I got everything to work great guys. I really appreciate the help that this forum always gives me!

---

### Post by decrepit on 2011-09-18
> **reaply said:**
> Ok this is the computer folder. I am not sure which one has the windows files?

[IMG]http://i53.tinypic.com/10yqp3r.png

This is the HD

[IMG]http://i51.tinypic.com/2imaur9.png

And this is the File System

[IMG]http://i52.tinypic.com/2agl1rn.png

Which one would I go to?

That's not the output of "fdisk -l"

If you do that we may see the windows partition.

---

