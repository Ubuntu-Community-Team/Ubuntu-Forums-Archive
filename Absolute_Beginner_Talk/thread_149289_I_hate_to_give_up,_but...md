---
title: "I hate to give up, but.."
date: 2006-03-23
forum: Absolute Beginner Talk
---

### Post by clareb on 2006-03-23
I'm really keen to switch over to ubuntu linux but I've just been going around in circles. I've spent hours trying to install ndiswrapper to get my usb wireless adaptor to work but I can't manage it. I've downloaded it onto the desktop and used
 tar zxvf ndiswrapper-version.tar.gz 
command but all I get are error messages:
tar: ndiswrapper-version.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
I told it to open instead of save when I downloaded too, but that didn't work out any better. 
I was hoping to learn something about computers by using linux but it all seems over my head, I need a real idiot's guide ;) Do you think I should just give up and go back to yucky windows?

---

### Post by gord on 2006-03-23
nah, there is a learning curve but it settles down once you get over the first few hurdles :)

all you are doing there wrong, is that you forgot to put a little - in there :). for example
```
tar -zxvf ndiswrapper-version.tar.gz
```
instead of 
```
tar zxvf ndiswrapper-version.tar.gz
```

---

### Post by clareb on 2006-03-23
Sorry, I get the exact same response with that command too. I have the files extracted in a folder, can anyone tell me what to do next. If I figured out how to partition the disk to get the whole thing installed surely I can do this???

---

### Post by taurus on 2006-03-23
You don't have to include the - in there!  It works either way...
```

tar zxvf ndiswrapper-version.tar.gz
-same as-
tar -zxvf ndiswrapper-version.tar.gz

```
I think the problem you are having is that you are NOT in the directory where that file is or you use the wrong name for the file!  I don't believe the file is called ndiswrapper-version.tar.gz!  You probably need to replace the "version" is the actual number for it!  

Assuming you are in the the directory where that file is, type 
```

tar xvzf ndiswrapper<hit the tab key>

```

---

### Post by barthel on 2006-03-23
[QUOTE=clareb]I'm really keen to switch over to ubuntu linux but I've just been going around in circles. I've spent hours trying to install ndiswrapper to get my usb wireless adaptor to work but I can't manage it. I've downloaded it onto the desktop and used
 tar zxvf ndiswrapper-version.tar.gz 
command but all I get are error messages:
tar: ndiswrapper-version.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
I told it to open instead of save when I downloaded too, but that didn't work out any better. 
I was hoping to learn something about computers by using linux but it all seems over my head, I need a real idiot's guide ;) Do you think I should just give up and go back to yucky windows?[/QUOTE]

It sounds like you're not in the correct directory when you're doing the tar command.

Try this:
[LIST=1]
[*]Open a new terminal (Applications->Accessories->Terminal)
[*]cd ~/Desktop
[*]ls
[*]tar zxvpf ndiswrapper-version.tar.gz
[/LIST]

When you run "ls", you should see your ndiswrapper tarball in the listing. ("ls" is like the WinDOS "dir" command).

Also, I added the "p" option to the tar command you're using. This will preserve the file permissions--generally a good thing to do, since otherwise executable files will not be saved with execute permission.

One other point--you can always include the full path in the tar command:
[INDENT]tar zxvpf ~/Desktop/ndiswrapper-version.tar.gz[/INDENT]

Good luck--it's a bit tough at first, but stick with Linux--the rewards are well worth it.

---

### Post by nalmeth on 2006-03-23
or right click on the package and use the graphical decompressor.

- EXTRACT

---

### Post by clareb on 2006-03-23
Thanks for all your quick responses. I did extract the tar.gz (right click - extract here) so now  have a folder on my desktop. I read the install instructions but I just don't understand this:

Make sure there is a link to the kernel source from
the modules directory. The command

  ls /lib/modules/`uname -r`/build

should have at least 'include' directory and '.config' file.

Can anyone enlighten me?

---

### Post by nalmeth on 2006-03-23
type that command into the terminal and see if it has a directory called 'include'. also look for that .config file. 
If you're not sure what you're looking at, post the output of that command here

I don't think you need be too worried about this.

---

### Post by clareb on 2006-03-23
I don't think I did this right but here's what happened:

clare@linuxubuntu:~$  ls /lib/modules/`uname -r`/build
ls: /lib/modules/2.6.12-10-386/build: No such file or directory
clare@linuxubuntu:~$

Thanks for the help.

---

### Post by barthel on 2006-03-23
[QUOTE=clareb]Thanks for all your quick responses. I did extract the tar.gz (right click - extract here) so now  have a folder on my desktop. I read the install instructions but I just don't understand this:

Make sure there is a link to the kernel source from
the modules directory. The command

  ls /lib/modules/`uname -r`/build

should have at least 'include' directory and '.config' file.

Can anyone enlighten me?[/QUOTE]

Looks like this package is a source tarball. However not to fear!

Ubuntu already has the kernal modules included. You just need the "userspace" package.

From the package description:
> Userspace utilities for ndiswrapper
Some wireless LAN vendors refuse to release hardware specifications or
drivers for their products for operating systems other than Microsoft
Windows. NdisWrapper makes it possible to use such hardware with Linux by
means of a loadable kernel module that "wraps around" NDIS (Windows network
driver API) drivers.

This package contains the userspace tools. The default Ubuntu kernel
already provides the required modules. If you use a custom kernel,
you might also need the kernel module package.

Since you're just starting, I doubt you've made a custom kernel, so...

[LIST=1]
[*]Go to System->Administration->Synaptic Package Manager
[*]Enter your password at the prompt.
[*]Click on the search button and search for "ndis"
[*]Select ndsiwrapper-utils for installation ([Ctrl]-i)and click "apply".
[/LIST]

Good luck!!

---

### Post by clareb on 2006-03-23
I did that this afternoon. It's installed but nothing I do is working. What would be the next step? The baby steps are great, thanks for your time.

---

### Post by barthel on 2006-03-23
[QUOTE=clareb]I did that this afternoon. It's installed but nothing I do is working. What would be the next step? The baby steps are great, thanks for your time.[/QUOTE]

Can I ask why you made a custom kernel? I've been using Slackware for years and always compiled a custom kernel, but have not had to so with Ubuntu. (It would take more fingers and toes than I have to count the number of times I had to reconfigure my custom kernel to get everything right and working. I eventually went so far as to write a build script that would automatically update my boot options so I could always go back to a working kernel.)

Unless you have some really esoteric hardware or other requirements, you might do well to reinstall the Ubuntu default kernel.

Regards

---

### Post by clareb on 2006-03-23
Mmm... I didn't know I had I thought I was installing the ndiswrapper off the install disk, I read I had to do that somewhere earlier. It's the only thing that worked out but I'm still not getting anywhere.

(Totally off topic - I read your profile - I like to know where the nice folks that are helping me are from - and we have the same birthday - I always said 13 was a lucky number..)

---

### Post by GMachine_24 on 2006-03-23
As someone who is still relatively new to Linux (both Ubuntu and Fedora FC4) I urge you not to give up on learning Linux. I remember when I first learned DOS and then Windows and it was aggravating and slow, also. We just tend to forget what it was like.

People in these forums are great. You will soon find others asking questions to which you know the answer and you will no longer feel like a 'noob.' 
And, you will soon find many new uses for Ubuntu/Linux that perhaps you would not have tried with Windows for one reason or another.

As they said on the X Files, "The Truth Is Out There." There are answers to your problems - you just need to tackle them one at a time and perhaps make sure to take a break now and then so your frustration doesn't overwhelm you.

Best of luck.

GM

---

### Post by barthel on 2006-03-23
[QUOTE=clareb]Mmm... I didn't know I had I thought I was installing the ndiswrapper off the install disk, I read I had to do that somewhere earlier. It's the only thing that worked out but I'm still not getting anywhere.
[/QUOTE]

OK, sorry, then I guess I misunderstood you. If you haven't done a custom kernel, then all you should need are the "userspace" utilities. "ndiswrapper-source" is the source code for the modules--you don't need to install that unless you made a custom kernel. (One that wasn't installed from the Ubuntu CD....)

If you installed "ndiswrapper-source", it would have suggested installing the kernel source, but that doesn't install a custom kernel--just the ability to *make* a custom kernel.

Granted, I don't have a wireless setup myself, but you should only need to install the "ndiswrapper-utils" package and it's dependencies.

> 
(Totally off topic - I read your profile - I like to know where the nice folks that are helping me are from - and we have the same birthday - I always said 13 was a lucky number..)

It's worse than that. I was born on a Friday the 13th. :D

---

### Post by clareb on 2006-03-23
I'm really determined not to give up, it's just frustrating when nearly everything I read is going over my  head. I don't think Windows does you any favours by spoon-feeding with wizards and that sort of thing. I like to know how things work, then if they go wrong there's a chance I can fix it, and feel like I've achieved something as well.

I thought I had installed the ndiswrapper-utils. It says it's installed, where do I go from there? Sorry to be so dense..

---

### Post by nalmeth on 2006-03-23
Great attitude and approach!
I think it ndiswrapper should show up in SYSTEM --> ADMINISTRATION as Windows Wireless Drivers or something. Did you download the driver you need for the card?

---

### Post by barthel on 2006-03-23
[QUOTE=clareb]I'm really determined not to give up, it's just frustrating when nearly everything I read is going over my  head. I don't think Windows does you any favours by spoon-feeding with wizards and that sort of thing. I like to know how things work, then if they go wrong there's a chance I can fix it, and feel like I've achieved something as well.

I thought I had installed the ndiswrapper-utils. It says it's installed, where do I go from there? Sorry to be so dense..[/QUOTE]

Oh believe me, I understand completely. When you're coming into a new community, there's a lot of things it's difficult to understand at first. (For example, I've used Slackware for so long that I was a bit stymied by some of the Ubuntu conventions... )

OK, so if you've got the ndiswrapper-utils installed, then the next step is configuration.

Unfortunately, I can't help much further, as I don't have wireless myself and have never worked with this kind of setup under Linux of any flavor.

However, there are several forum threads I found when searching for "ndiswrapper".

I also found this Ubuntu wiki page: [https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper]("https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper") which may help you further along the path to getting this working.

I'd also suggest starting a new thread which includes a specific question on ndiswrapper in the subject for further followup. That will help attract people who have worked with this type of setup and are more qualified to help.

Good luck, and welcome to the community!

---

### Post by clareb on 2006-03-23
I copied the driver files from the modem install cd into a folder, they don't seem to be doing much at the moment. I know I'm supposed to get them and the nsidwrapper together so they can sort out my little problem, I just don't know how to do it.
Thanks again for all the help - it's really encouraging me not to give up.

---

### Post by GMachine_24 on 2006-03-23
[QUOTE=clareb]I'm really determined not to give up, it's just frustrating when nearly everything I read is going over my  head. I don't think Windows does you any favours by spoon-feeding with wizards and that sort of thing. I like to know how things work, then if they go wrong there's a chance I can fix it, and feel like I've achieved something as well.

I thought I had installed the ndiswrapper-utils. It says it's installed, where do I go from there? Sorry to be so dense..[/QUOTE]


I've been banging my head for 2-3 days trying to get my external firewire drive working. Finally, today, I did it. If you want to read the back-and-forth between me and an Ubuntu moderator who was helping me and how fed up I got . . . but did not quit . . . you might not feel so bad. The link is below . . and let me tell you..... when you solve the problem, it feels GREAT.

[http://www.ubuntuforums.org/showthread.php?t=147565](http://www.ubuntuforums.org/showthread.php?t=147565)

GM

---

### Post by clareb on 2006-03-23
Thanks for that - I'm really looking forward to finally cracking it - I have my happy dance planned. I think I'll take Barthel's advice and post a new thread about ndiswrapper and the rest..

Thanks for everyone's time and patience.

---

