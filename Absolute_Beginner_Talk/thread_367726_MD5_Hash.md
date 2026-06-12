---
title: "MD5 Hash"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by MentallyInept on 2007-02-22
I cannot for the life of me get a download of ubuntu 6.10 (Intel i386) to pass an MD5 Hash Check.

I downloaded and burned the iso to CD yesterday and installed ubuntu on my work PC for the heck of it. Since then, I have encountered all kinds of crazy errors like the Terminal Crashing when I try to type, Firefox randomly crashing, my system rebooting out of nowhere. The list goes on.

I got the system to be stable enough to re-download the iso. And this time I was going to check the MD5 sum before I burn it.

When I do the MD5 sum on it I get: 
3bef9ba6d1d546f5a565c2becc24e000  ubuntu-6.10-desktop-i386.iso

when it should be:
b950a4d7cf3151e5f213843e2ad77fe3  ubuntu-6.10-desktop-i386.iso

I will try re-downloading the .iso AGAIN, but I do not have high hopes for this. Is the MD5 sum for the .iso updated?

---

### Post by igknighted on 2007-02-22
> **MentallyInept said:**
> I cannot for the life of me get a download of ubuntu 6.10 (Intel i386) to pass an MD5 Hash Check.

I downloaded and burned the iso to CD yesterday and installed ubuntu on my work PC for the heck of it. Since then, I have encountered all kinds of crazy errors like the Terminal Crashing when I try to type, Firefox randomly crashing, my system rebooting out of nowhere. The list goes on.

I got the system to be stable enough to re-download the iso. And this time I was going to check the MD5 sum before I burn it.

When I do the MD5 sum on it I get: 
3bef9ba6d1d546f5a565c2becc24e000  ubuntu-6.10-desktop-i386.iso

when it should be:
b950a4d7cf3151e5f213843e2ad77fe3  ubuntu-6.10-desktop-i386.iso

I will try re-downloading the .iso AGAIN, but I do not have high hopes for this. Is the MD5 sum for the .iso updated?

Are you downloading it via torrent or from a server?  Try using one of the Ubuntu mirrors (a different one if you are already using one).

---

### Post by mahy on 2007-02-22
For what it's worth, download the iso via torrent. You'll get the correct hash that way.

---

### Post by MentallyInept on 2007-02-22
> **igknighted said:**
> Are you downloading it via torrent or from a server?  Try using one of the Ubuntu mirrors (a different one if you are already using one).

First download was from the torrent, Second was ddl from the site. I am trying the site again. I will start a torrent download on top of that.

---

### Post by MentallyInept on 2007-02-22
OK... an update.

I redid the direct download and got the same result for MD5:
b950a4d7cf3151e5f213843e2ad77fe3  ubuntu-6.10-desktop-i386.iso

I am waiting for the Torrent to finish and I will post the results of that...

---

### Post by mahy on 2007-02-22
If you're downloading it via torrent, you can also check the ISO's hash with the one displayed in the torrent client. Hope it works for you.

---

### Post by MentallyInept on 2007-02-22
Failure once again...

md5sum returns this for the torrent I downloaded:
7294242a2c4ed2e6536449ebbebfeea3  ubuntu-6.10-desktop-i386.iso

---

### Post by mcduck on 2007-02-22
What kind of hardware do you have? At least some nForce-based motherboards have built-in firewall that is known to corrupt downloads.. In that case you should turn it off in BIOS.

Also bad RAM could of course cause corruption.

---

### Post by MentallyInept on 2007-02-22
> **mcduck said:**
> What kind of hardware do you have? At least some nForce-based motherboards have built-in firewall that is known to corrupt downloads.. In that case you should turn it off in BIOS.

Also bad RAM could of course cause corruption.

This is a standard Dell Optiplex 620 that is used, it is not an nForce mobo. It uses Intel Integrated Graphics.

I don't believe it is bad ram but I don't know how to check for that without a utility.

---

### Post by steve.horsley on 2007-02-22
If you're in the UK, email me your address at [email]steve.horsley@gmail.com[/email] and I'll bung a CD in the post.

---

### Post by igknighted on 2007-02-22
What program are you burning with?  If you can, download the Alcohol 120% trial and try that, its a great piece of software (second to only K3B).

---

### Post by MentallyInept on 2007-02-22
Ok, I just looked over this thread, and I realized that it passed on the second Direct Download.

I got the correct one mixed up in my head because I thought it was the 3b... not the b... one... le sigh.

Check the username, that is all, good day sirs, thanks for the help.

---

### Post by entropyfoe on 2007-02-24
I often get bum iso md5 sums.  Just a bad download. 
 What speed was the dl?
If I see a slow dl, i suspect errors.  Check different mirrors for the highest speed.

Then burn (ironically) at a low speed.  4-8X.

Or go to:
[http://www.linuxcd.org/](http://www.linuxcd.org/)
For literally a few dollars you can get a good CD sent.

Check your memory with MEMTEST bootable at grub in xubuntu or Mepis for example.
Run a few hours without errors, you are probably ok.  Run 12-24 hours, without errors means your RAM is OK.
-Jay

---

### Post by net4home on 2007-07-28
From what I see there has been issues with the md5 hash.  I have downloaded Ubuntu 6.06 LTS, 6.10 and 7.04 both desktop and server versions.  The only version I have yet to make work after downloading is the 6.06 LTS version.  I have downloaded the server versions of 6.10 and 7.04 several times and have had problems every time.  When I check the MD5 Hash on the download itself it shows that the download MD5 Hash matches to what it should from the site I've downloaded it from.  This is not site specific as I have downloaded it from serveral different sites in the North America section.  I also have burned serveral CD's trying to find out where the problems occur.  After careful checking it seems that the i386 ISO files for the server versions of the 6.10 and the 7.04 may have the wrong MD5 Hash in the text file on the CD.  I say that only because the downloads show that they passed the MD5 Hash tests, but after burning them to a CD-R at 4x in Mode 1 format and before installing I boot from the CD and run the Check CD-ROM for problems.  Upon running this I will get a red screen telling me that the CD-R is no good.
 
Now I've read in these posts that it has been suggested to use another CD Burning program, the only issue with this is that I've burned so many other CD-R's before and since that have worked, that I've ruled this out as being a source of the problem.  Can someone who is on the development of Ubuntu please either verify that this is either true and see what can be done to fix it or please let us who seem to be having this issue know how to fix it if possible.  
 
I know I could go and order a CDRom and I'm sure it would be OK, but if this is the case why offer a download option.  Please understand Ubuntu is the only Distro that I've found that I like and have been using it for about a year now and I'm moving from being in the MS world, for a long time, into the Linux world.  
 
Thank you in advance for your answers and support.
 
net4home
(Kevin)

---

### Post by kings121 on 2008-05-06
> **steve.horsley said:**
> If you're in the UK, email me your address at [email]steve.horsley@gmail.com[/email] and I'll bung a CD in the post.

hey steve i,m new here i sent an email to you about the problem i,m havin with Ubuntu....but i,ll say it here just in case.....i downloaded a few Ubuntu Iso software burn them to cd but not able to boot from them.....what i would like to do is put Ubuntu beryl on 2 pc amd and intel....i dont know how to check the MD5 checksum on these downloaded software.....so if you can help me i would greatly appreciate it......i,m in sweden


what i would like to know also is if these OS will enable me to change my keyboard to swedish......

---

