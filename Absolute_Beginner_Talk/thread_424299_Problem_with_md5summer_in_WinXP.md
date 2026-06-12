---
title: "Problem with md5summer in WinXP"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-04-26
When I try to run md5summer in WinXP to check my feisty download, I am told: [B]md5summer.md5 is not a valid Win32 application.
 
[/B]What must I do to get md5summer working so that I can check my Feisty download. I've seen this before on other programs that I downloaded but didn't know how to resolve the problem. I just deleted the program. Md5summner I would like to have.

Thanks for your help.
kh

---

### Post by taurus on 2007-04-26
Maybe this guide will give you a hint about md5sum.

[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by kittyhawk63 on 2007-04-26
> **taurus said:**
> Maybe this guide will give you a hint about md5sum.

[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

That's where I am right now. He doesn't say what to do if you have my problem. He is assuming it works.

Thanks.
kh

---

### Post by aidanr on 2007-04-26
> **kittyhawk63 said:**
> **md5summer.md5 is not a valid Win32 application.**


thats like a text file containing the md5 sum, you want to click on the one that says md5summer or md5summer.exe, the one with the red and blue icon

---

### Post by kittyhawk63 on 2007-04-26
> **aidanr said:**
> thats like a text file containing the md5 sum, you want to click on the one that says md5summer or md5summer.exe, the one with the red and blue icon

Ok. I'll check to see if that is what I am doing wrong. 

Edit: It is the right one. It is the icon that was made when I started the install of the download. 
Thanks.
kh

---

### Post by 5-HT on 2007-04-26
I struggled with this too (issue is in PATH variable: basically Windows cannot locate the md5summer executable to run it). There are two options:

1. Run md5summer from the directory containing BOTH the md5summer.exe and all the files you want to generate md5 hashes for 

i.e., if you have the .iso on your desktop, md5summer.exe needs to be on your desktop

OR

2. Add the directory containing the md5summer.exe to your PATH (I haven't run windows for a while, so I'm unsure exactly where you set the PATH in different versions of Windows...but I believe it's somewhere in 'System Properties' and either 'advanced' or 'environmental settings'. I used to prefer this option as you can then run the program from any directory in which you might have saved the files you want to generate hashes for.

i.e, if you put md5summer.exe in c:\apps, you need to add c:\apps to your PATH

md5summer is truly a great program! Let me know if you have any further issues, I can always get access to a windows computer and double check for you.
[B]

EDIT: updated my post kittyhawk63, hope it's a little more clear now[/B]

---

### Post by kittyhawk63 on 2007-04-26
> **5-HT said:**
> I struggled with this too. There are two options:

1. Run md5summer from the directory containing BOTH the md5summer.exe and all the files you want to generate md5 hashes for

**I understand this part. I'll give it a go.**

OR

2. Add the directory containing the md5summer.exe to your PATH (I haven't run windows for a while, so I'm unsure exactly where you set the PATH in different versions of Windows...but I believe it's somewhere in 'System Properties' and either 'advanced' or 'environmental settings'

**Not sure what you mean by setting path. WinXP is freshly installed and I let it set everything automatically with default settings.**

md5summer is truly a great program!

[B]I'll take your word for it. :)

kh
[/B]

---

### Post by kittyhawk63 on 2007-04-26
I give up! ](*,)  I thought that I would never say that. 

I can't download as an upgrade without my video freezing. In WinXP, I can't get the Feisty ISO to burn using three different CD burners. I had no problem burning Dapper. That was two months ago. Maybe my CD-RW Rom drive has gone bad since then. As things have gone since starting this Linux adventure, I would not be surprised. I don't know. I can play audio. But I can't get it to burn for some reason. :mad:

I will have to wait until my ordered Feisty ISO CD arrives. That will be a number of weeks from now. Unless, someone is on their toes and gets it in the mail pronto. But as things have gone this past two months trying to get Ubuntu to stabilize on my machine, it will probably be a month or more before the CD arrives. I've been patient enough to get this dad burn program to work this far, a little while longer won't be too bad. :(

I will be in the wings watching from afar, unless I can give some noob a little advice on something that I have picked up along the way. :)

Thanks to all of you over the past two months who have offered much assistance. I have appreciated it very much. =D>

Edit: My CD-R/RW Rom Player had gone bad. I replaced it and now I can burn ISOs again.
kh ):P

---

### Post by Sef on 2007-04-26
1) Have you read how to write ISO files to a cd?

2) Have you downloaded and burned the iso with [ISO Recorder]("http://isorecorder.alexfeinman.com/isorecorder.htm")?

---

### Post by kittyhawk63 on 2007-04-26
> **Sef said:**
> 1) Have you read how to write ISO files to a cd?

2) Have you downloaded and burned the iso with [ISO Recorder]("http://isorecorder.alexfeinman.com/isorecorder.htm")?

Yes and yes.
Thanks for asking though.
kh

---

### Post by taurus on 2007-04-26
Do you know that you can access your Ubuntu from Windows with [http://www.fs-driver.org?](http://www.fs-driver.org?)  Download feisty from Windows.  Then, copy it to Ubuntu (I assume you are running Edgy right now), run a checksum in Ubuntu.

```
md5sum filename.iso
```
If it passes, then burn it with k3b, gnomebaker, or any other burn app in Ubuntu.

---

### Post by kittyhawk63 on 2007-04-26
> **taurus said:**
> Do you know that you can access your Ubuntu from Windows with [http://www.fs-driver.org?](http://www.fs-driver.org?)  Download feisty from Windows.  Then, copy it to Ubuntu (I assume you are running Edgy right now), run a checksum in Ubuntu.

```
md5sum filename.iso
```If it passes, then burn it with k3b, gnomebaker, or any other burn app in Ubuntu.

My Linux hard drive is kaput. I mean by this that there is no working Linux on it. I tried installing it yesterday with an abbreviated download that was automatically downloaded while I was in Edgy. That had never happened before. I had always received the regular ISO. Anyway, I installed it using the install and there were only a few files on it. Most were still to be downloaded. In fact, almost 700 files. My computer kept crashing with my long time nemesis of screen freezes. After four tries, I finally gave up and downloaded the regular ISO to WinXP. I have not been able to burn the image to CD. I had no problem doing it with Dapper. I think my CD Rom Player has possibly gone bad, but I have no way of telling. I can't get md5sum to work either. Not my day. Not my week. In fact, not my two months. But I'm not giving up. I will just wait until the ordered CD arrives and try again. I will more than likely buy one of the Nvidia cards you mentioned the other day. I'm tired of fighting with ATI. That is where all my problems starts.
kh

Edit: I'm reading about accessing Linux from windows right now. Thanks for the heads up.

---

### Post by taurus on 2007-04-26
I assume you still have the Feisty ISO on your Windows.  What if you boot from an old Ubuntu LiveCD (whether it's Dapper or Edgy), mount the Windows partition, and run checksum of the ISO file from the LiveCD?

---

### Post by kittyhawk63 on 2007-04-26
> **taurus said:**
> I assume you still have the Feisty ISO on your Windows.  What if you boot from an old Ubuntu LiveCD (whether it's Dapper or Edgy), mount the Windows partition, and run checksum of the ISO file from the LiveCD?

I have Feisty ISO on my Desktop in WinXP.

I have a Dapper LiveCD. I know that I can get it to stabilize with my ATI card. I never was able to get Edgy to stabilize with my ATI card.

Not sure what you are suggesting when it comes to running the checksum of the ISO file. I tried running md5sum. I couldn't get it to work. Probably due to my ignorance rather than a fault of the program.

kh

---

### Post by taurus on 2007-04-26
Boot your computer with Dapper LiveCD.  Then, mount your Windows partition, assuming it's /dev/hda1, with

```
sudo mkdir /media/windows
sudo mount -a ntfs /dev/hda1 /media/windows -o nls=utf8,umask=0222
```
Then, change directory to where you've saved the Feisty ISO image, assuming it's in "Program Files".

```
cd "/media/windows/Program Files"
md5sum ubuntu-7.04-desktop-i386.iso
```

---

### Post by kittyhawk63 on 2007-04-26
> **taurus said:**
> Boot your computer with Dapper LiveCD.  Then, mount your Windows partition, assuming it's /dev/hda1, with

```
sudo mkdir /media/windows
sudo mount -a ntfs /dev/hda1 /media/windows -o nls=utf8,umask=0222
```Then, change directory to where you've saved the Feisty ISO image, assuming it's in "Program Files".

```
cd "/media/windows/Program Files"
md5sum ubuntu-7.04-desktop-i386.iso
```

Ok.
I'm off to Linux world, again. See you on the other side. I am leaving WinXP until I get your instructions working. As you know, this will take some time. I printed out these instructions.
kh

---

### Post by Maxtine on 2007-04-26
Hi a newbe here. There seems to be a real problem with using the ISO to install. I don't know about anyone else, but when I downloaded the ISO (ubuntu.com/feisty/ubuntu-7.04-desktop-i386.iso)  the file size was  over 714MB this maybe causing most of the problems, I don't know. Using two different programs I had problems burning to a CD however I went to [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto) and downloaded, installed and followed the directions for using the Infra Recorder. No problems.
Next I did the same thing that I did for windos. A clean install delete all the partitions and this time create a separate /home checked all cables. Clean install worked next installed Automatix2 everything loaded no problems
I hope that this may help someone

---

### Post by kittyhawk63 on 2007-04-27
Well, with a little bit of persistence and your help guys, I was finally able to get md5sum to work and InfraRecorder. I had to use the Express feature of InfraRecorder to burn the Feisty ISO. The main CD burner feature of InfraRecorder would not locate my CD-R/W player. Tis strange, indeed.
Now to try and get my hard drive formatted right and partitioned to accept Feisty. I was unable to install Dapper earlier. something wrong with the hard drive. I tried fdisk as well as the utility disk that came with the hard drive. So far, can't figure out what to do to make it where I can install the ISO.
Had this trouble some time back. Should have written down what I did. Of course, it could have been a fluke and just started working.

Anyone know how to work with Seagate HDDs? :confused:
kh

---

