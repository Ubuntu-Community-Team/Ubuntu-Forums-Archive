---
title: "Won't boot from DVD drive"
date: 2006-01-23
forum: Absolute Beginner Talk
---

### Post by Cousindaddy on 2006-01-23
This is my first attempt at installing Ubuntu (or any Linus distro for that matter).  I dloaded both the "live" and the "install" iso files from Ubuntu.com.  I have reset my BIOS to boot from the DVD drive.  But nothing happens...the system proceeds directly to Windows (XP Pro BTW).  I ran md5sum on the "live" version and was given a long string of characters but no error messages of any sort.  Is there something that needs to be done to the iso file prior to burning it to CD?

Someday I hope to be a Linux newbie, right now I'm still a zygote dreaming of the day I can excise the cancer from my hard drive that is Microsoft Windows.

(Appologies if the answer to this lies elsewhere on this site.  I read through the first 5 pages and searched on relevant keywords to no avail. I know it is very tiresome answering the same question over and over.)

---

### Post by dueY on 2006-01-23
[QUOTE=Cousindaddy]This is my first attempt at installing Ubuntu (or any Linus distro for that matter).  I dloaded both the "live" and the "install" iso files from Ubuntu.com.  I have reset my BIOS to boot from the DVD drive.  But nothing happens...the system proceeds directly to Windows (XP Pro BTW).  I ran md5sum on the "live" version and was given a long string of characters but no error messages of any sort.  Is there something that needs to be done to the iso file prior to burning it to CD?

Someday I hope to be a Linux newbie, right now I'm still a zygote dreaming of the day I can excise the cancer from my hard drive that is Microsoft Windows.[/QUOTE]

Did you burn them as images?  You have to burn them as an image.

I believe there is a trial of Nero that can do this if your burning software can't.

---

### Post by Cousindaddy on 2006-01-23
[QUOTE=dueY]Did you burn them as images?[/QUOTE]

That's probably the problem.  Do I keep the same file name?  Are there any other things I should do before I light the match?

---

### Post by dueY on 2006-01-23
[QUOTE=Cousindaddy]That's probably the problem.  Do I keep the same file name?  Are there any other things I should do before I light the match?[/QUOTE]

You can keep the same name.  Just make sure you burn it as an image and not as a CD containing the file whatever.iso.  Unless you need another coaster :p

---

### Post by Cousindaddy on 2006-01-23
Okay...I think...  The file name is 
                     "ubuntu-5.10-live-i386.iso"
Just use the same name, right?

---

### Post by dueY on 2006-01-23
[QUOTE=Cousindaddy]Okay...I think...  The file name is 
                     "ubuntu-5.10-live-i386.iso"
Just use the same name, right?[/QUOTE]

Yeah sure when you burn it as an image I don't think it matters.

---

### Post by Kevbb on 2006-01-23
In NERO you have to chose "Burn image to disk" nothing else.

Cheers.

---

### Post by Cousindaddy on 2006-01-23
Thank you both very much...that solved the problem and I am now excited to say that this is my first post using Ubuntu...(I feel giddy and a bit lightheaded...whew!)
Anyway...next question...how do I begin to "purify" my system of Windows?  Do I have to call an exterminator?  My HD is 120GB..3 partitions...what's my next step?
(gawd, this must be what it feels like to be released from prison!)
Again, thanks so much!

---

### Post by dueY on 2006-01-23
[QUOTE=Cousindaddy]Thank you both very much...that solved the problem and I am now excited to say that this is my first post using Ubuntu...(I feel giddy and a bit lightheaded...whew!)
Anyway...next question...how do I begin to "purify" my system of Windows?  Do I have to call an exterminator?  My HD is 120GB..3 partitions...what's my next step?
(gawd, this must be what it feels like to be released from prison!)
Again, thanks so much![/QUOTE]

Are you sure you want to completely remove Windows?  If so you're going to have to format that drive into something other than NTFS.  ```
sudo apt-get install gparted
``` might help!

---

### Post by Cousindaddy on 2006-01-23
[QUOTE=dueY]Are you sure you want to completely remove Windows? [/QUOTE]
Yes, I am sure...although, with caveat...I think it best to do it slowly to avoid any major catastrophy.  
I'm having difficulty setting my clock to the correct time...I'm able to select the time zone without problem, yet the displayed time is 1 hour behind...no biggee...in fact it makes me feel a bit younger... Also, I'm not really sure if I'm operating from the CD or has Ubuntu installed itself?

Back to the subject of removing windows,  how do I pull all of the files over that I want to keep and toss the rest? 

[QUOTE=dueY]If so you're going to have to format that drive into something other than NTFS.[/QUOTE]
I assume Ubuntu will do that for me (formatting the drive).

[QUOTE=dueY]```
sudo apt-get install gparted
``` might help![/QUOTE]

Where do I find this and how do I run it?  Is it command line?

Again, thanks for your help!

---

### Post by dueY on 2006-01-23
[QUOTE=Cousindaddy]Also, I'm not really sure if I'm operating from the CD or has Ubuntu installed itself?
[/QUOTE]

Well, in an earlier post you said the file name was  "ubuntu-5.10-live-i386.iso" so if you are using that burned CD then you did not install Ubuntu.  That is a LIVE CD, which is basically a CD used to see if a) your system is capable of running Ubuntu b) Ubuntu is even something you would be interested in installing.  Nothing is being written to your harddrive with the LIVE CD.

---

