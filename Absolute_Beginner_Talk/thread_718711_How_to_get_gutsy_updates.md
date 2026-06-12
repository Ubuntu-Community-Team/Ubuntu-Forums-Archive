---
title: "How to get gutsy updates"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by swarup on 2008-03-08
i have just installed gutsy on my laptop and setup my broadband connection. I thought that by going online the update icon will automatically appear to download all the available gutsy updates. But no such icon has appeared.what do i have to do in order to get all the latest updates? And what do i have to do so that the updates icon will automatically appear in the future?

---

### Post by st33med on 2008-03-08
Try:
```
sudo apt-get update
```

Usually, that pops up the update manager if there is anything to update. If it still does not pop up:

```
sudo apt-get upgrade
```

That should upgrade anything. If you still have problems, just post again!

---

### Post by jan quark on 2008-03-08
also make sure you have enabled all the software sources

go to 

system > administration > software sources

and enable everything except source code and cd

then run 
```

sudo apt-get update
```
```
sudo apt-get upgrade
```

---

### Post by st33med on 2008-03-08
There also maybe another problem in which kron is not starting up at boot. But, it could also be that there has not been any updates in a while.

---

### Post by swarup on 2008-03-08
> **jan quark said:**
> also make sure you have enabled all the software sources

go to 

system > administration > software sources

and enable everything except source code and cd

then run 
```

sudo apt-get update
```
```
sudo apt-get upgrade
```

I went to software sources as you directed, and enabled everything except source code and cd. Upon doing so, it wanted to download what seemed like various lists of directories. And in the end, it gave the following error:
> 
The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg:) Cannot initiate the connection to archive.ubuntu.com:80 (91.189.88.45). - connect (101 Network is unreachable) [IP: 91.189.88.45 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_IN.bz2:](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_IN.bz2:) Cannot initiate the connection to archive.ubuntu.com:80 (91.189.88.45). - connect (101 Network is unreachable) [IP: 91.189.88.45 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_IN.bz2:](http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_IN.bz2:) Cannot initiate the connection to archive.ubuntu.com:80 (91.189.88.45). - connect (101 Network is unreachable) [IP: 91.189.88.45 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_IN.bz2:](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_IN.bz2:) Cannot initiate the connection to archive.ubuntu.com:80 (91.189.88.45). - connect (101 Network is unreachable) [IP: 91.189.88.45 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_IN.bz2:](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_IN.bz2:) Cannot initiate the connection to archive.ubuntu.com:80 (91.189.88.45). - connect (101 Network is unreachable) [IP: 91.189.88.45 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz:) Cannot initiate the connection to archive.ubuntu.com:80 (91.189.88.45). - connect (101 Network is unreachable) [IP: 91.189.88.45 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz:) Cannot initiate the connection to archive.ubuntu.com:80 (91.189.88.45). - connect (101 Network is unreachable) [IP: 91.189.88.45 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz:) Cannot initiate the connection to archive.ubuntu.com:80 (91.189.88.45). - connect (101 Network is unreachable) [IP: 91.189.88.45 80]
[http://archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz:) Cannot initiate the connection to archive.ubuntu.com:80 (91.189.88.45). - connect (101 Network is unreachable) [IP: 91.189.88.45 80]

I should also add that if I go to Add/Remove programs, there too it is not allowing me to download anything. It keeps saying it needs to reload the list of available software, and I need an internet connection. But I HAVE an internet connection. I am online right now, as I am writing to you. So why does it not accept that?

---

### Post by swarup on 2008-03-08
[duplicate message]

---

### Post by swarup on 2008-03-08
And now I find that the whole "software sources" window with the boxes I checked, is greyed out and will not allow to be closed. If I try to close out the window, it downloads 16 files and then the following error message appears:

> The information about available software is out-of-date

To install software and updates from newly added or changed sources, you have to reload the information about available software.

You need a working internet connection to continue.

And then the "software sources" window remains greyed out. And if I try to close it out again, then it goes through the motion of downloading the same 16 files again, and then gives the same error message. When they are downloading, it looks like it is really being downloaded with  the progress bar and all. But then it seems like they are not downloaded, because the same above error message appears.

And another strange thing is happening. Despite the fact that I have already logged into the support forum tonight, sometimes when I try to post a reply, it asks me to log in again-- as if it does not remember that I was already logged in.

---

### Post by swarup on 2008-03-08
> **st33med said:**
> Try:
```
sudo apt-get update
```

Usually, that pops up the update manager if there is anything to update. If it still does not pop up:

```
sudo apt-get upgrade
```

That should upgrade anything. If you still have problems, just post again!

Here below is the output from when I did the above. From the looks of it, it would seem like there is nothing to download. But I do not believe it. Because I have just now installed Gutsy-- so it should be needing to update all the changes and updates since October of 2007 when Gutsy was introduced, right? Something doesn't seem right.

```
baba@BABA:~$ sudo apt-get update
[sudo] password for baba:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_IN
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_IN
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_IN
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_IN
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages
Fetched 1B in 2s (0B/s)  
Reading package lists... Done
baba@BABA:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by st33med on 2008-03-08
Possibly because you just burned it? I think the Live CDs are updated as often as when it Ubuntu installations are updated.

---

### Post by swarup on 2008-03-08
> **st33med said:**
> Possibly because you just burned it? I think the Live CDs are updated as often as when it Ubuntu installations are updated.

I burned this cd on January 8th of this year. There should have been plenty to download.

Something odd is going on. Why can't I download any software either? And why is it saying that I need an internet connection to update the list of software with for downloads-- when I HAVE an internet connection and I AM on line.

---

### Post by ugm6hr on 2008-03-08
> **st33med said:**
> Possibly because you just burned it? I think the Live CDs are updated as often as when it Ubuntu installations are updated.

Not true.  The Ubuntu download .iso remains unchanged for the duration of its support, except for LTS versions (which now have updates at unspecified intervals).

@swarup:

Anyway - try this: [http://ubuntuforums.org/showpost.php?p=4030951&postcount=16](http://ubuntuforums.org/showpost.php?p=4030951&postcount=16) (start from the Add/Remove... bit)

---

### Post by swarup on 2008-03-08
> **ugm6hr said:**
> Not true.  The Ubuntu download .iso remains unchanged for the duration of its support, except for LTS versions (which now have updates at unspecified intervals).

@swarup:

Anyway - try this: [http://ubuntuforums.org/showpost.php?p=4030951&postcount=16](http://ubuntuforums.org/showpost.php?p=4030951&postcount=16) (start from the Add/Remove... bit)

Yes, someone else yesterday on this thread (see above) had suggested this. So I had gone to that page and made the changes then, as directed by you below:

> In Applications->Add/Remove... (presumably where you were having the problems before):
Click Preferences
A new window Software Sources will open
Select the Ubuntu Software tab
Make sure the top 4 boxes are ticked & Click Close

So that is all done. I went back to try a download just now. I selected to download the Wine emulator. It accepted to do so, and is actually in the process of downloading it now. We'll see if it succeeds in the end or is just making a fake show of it like it did yesterday. It is showing "Downloading file 3 of 3", but the download rate is so slow, something is definitely wrong. Mostly it shows "download rate unknown" (ie too slow to show), and then sometimes it shows in only b/s speed ie 2543 b/s and says it will take some huge number of days to finish. Sometimes it gets as high as 14 kb/s briefly. --But my connection is ADSL pppoe, it is a broadband connection. So why is it so slow???

---

### Post by ugm6hr on 2008-03-09
> **swarup said:**
> Yes, someone else yesterday on this thread (see above) had suggested this. So I had gone to that page and made the changes then, as directed by you below:

Sorry.

I had only partly read the thread.... Always a dangerous move when helping!

One other thing - in the Software Sources box, select "Main Server" if you haven't already, and then click on the Reload button in Synaptic Package Manager.

Then try again to see if it is any faster.

I have found that the Main Server is a lot faster than the UK one, certainly.  Perhaps it is the same with other regional servers?

---

### Post by louieb on 2008-03-09
> **swarup said:**
>  --But my connection is ADSL pppoe, it is a broadband connection. So why is it so slow???

One thing you might try.
System>Administration>Software Sources
Download from>Other>Select best server.

This does a speed test on the various mirrors and selects the one that fastest at the time.  Don't know if it will help but its worth a try.

---

### Post by bumanie on 2008-03-09
I had the same problem with gutsy initially (now using hardy). There was not an update icon or it flashed up occasionally and then disappeared. Fixed it by following this thread, answered by bytejuggler regarding the glibc6 problem. [http://ubuntuforums.org/showthread.php?p=4112658](http://ubuntuforums.org/showthread.php?p=4112658)
After following that I got 122 updates offered and they all downloaded.

---

### Post by swarup on 2008-03-09
Many thanks for the various above suggestions! I will experiment with the Main Server, and see how that works. I just tried the "Select Best Server" option, but it was unable to work properly. It checked 175 of 185 mirrors, and then gave an error message saying 'unable to complete check, and to check my internet connection'. But I'll try with Main Server for now, and see how that works. 

I'll also check out the thread mentioned by bumanie and see if that helps.

I should also mention that spiderbatdad sent me a link to a post he wrote 3 weeks ago (post #1 in that thread)

[http://ubuntuforums.org/showthread.php?t=693309](http://ubuntuforums.org/showthread.php?t=693309)

...which I have found immensely helpful. After following the directions there, I was able to download 205 gutsy updates. My internet connection, although broadband, was slowed down by intermittent pauses which made the download last virtually all day. I am new to this ADSL company, and so don't know whether this is perhaps a problem caused by it or rather by my pppoe setup, or something about the mirrors. But I will experiment further and see in the coming days, how downloads go.

Thanks again everyone, for your suggestions!

---

