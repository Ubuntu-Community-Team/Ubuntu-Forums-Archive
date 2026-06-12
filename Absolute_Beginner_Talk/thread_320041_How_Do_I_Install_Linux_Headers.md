---
title: "How Do I Install Linux Headers?"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by linux4me on 2006-12-16
I am trying to install the drivers for my Intel 536EP internal fax/modem according to the wiki:

[https://help.ubuntu.com/community/DialupModemHowto/Intel536EP](https://help.ubuntu.com/community/DialupModemHowto/Intel536EP)

And I got to the point of running "make 536" to compile the driver, but I get the following error in Terminal:

 Module precompile check
   Current running kernel is: 2.6.15-27-386
   /lib/modules...   autoconf.h does not exist
   please install kernel source

Okay, I figure that means I need to install kernel source. I did some reading and it appears all I really need is the kernel headers, not the entire source. Sooo...

I used apt and Synaptic to look for kernel headers, which appear to be called "linux-headers" but could only find earlier versions, not 2.6.15-27-386. The latest I found were 2.6.15-23-386.

My questions are:

[LIST=1]
[*]Do I need the 2.6.15-27-386 drivers to match my installation or the earlier 2.6.15-23-386?
[*]Is a simple "sudo apt-get install linux-headers-2.6.15-x-386" all I need to have the headers installed in the correct location so I can re-run "make 536" or is there another step in installing the headers?
[/LIST]

Thanks in advance!

---

### Post by maxamillion on 2006-12-16
You will need the linux headers to match the version of the kernel you are running. There are 2.6.15-27 i386 headers in the repo, [http://packages.ubuntu.com/dapper/devel/linux-headers-2.6.15-27-386](http://packages.ubuntu.com/dapper/devel/linux-headers-2.6.15-27-386) and when they install they will be put in the path so that make file shouldn't have any issue finding them.

/me

---

### Post by Bachstelze on 2006-12-16
```
sudo apt-get install linux-headers-$(uname -r)
```

---

### Post by linux4me on 2006-12-16
I tried downloading and installing (opening) with gDebi from the link you gave me, but I get "error: dependency is not satisfiable: linux-headers-2.6.15-27". I checked the dependencies (coreutils, libc6) in Synaptic to confirm they are installed, and they are. The versions are also greater than those required.

I tried the command 

sudo apt-get install linux-headers-$(uname -r)

and got the error

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-headers-2.6.15-27-386

which was the same problem I was having earlier when I tried apt.

I suspect I am doing something really simple wrong, but I'm only three two days into Ubuntu and still stumbling. I REALLY appreciate the help!

---

### Post by linux4me on 2006-12-16
I figured out the "dependency not satisfiable" error. It was right there for me the whole time, but since the file it listed in the error was "2.6.15-27-386", I didn't realize it was a different file than I was trying to install.

I then realized I needed to activate some other repositories--which was the reason Synaptic wasn't able to find the packages I needed in the first place--and now I have the kernel headers installed and can try the modem driver installation again!

Thanks for the help.

---

### Post by az on 2006-12-16
> **linux4me said:**
> I figured out the "dependency not satisfiable" error. It was right there for me the whole time, but since the file it listed in the error was "2.6.15-27-386", I didn't realize it was a different file than I was trying to install.

I then realized I needed to activate some other repositories--which was the reason Synaptic wasn't able to find the packages I needed in the first place--and now I have the kernel headers installed and can try the modem driver installation again!

Thanks for the help.

For those who do not have internet access, you can install the headers from the install cd.  When you are at your ubuntu desktop, just insert the cd and the package manager will start - you will then be able to install the linux-headers from the cd.

If you use the linux-headers-386 meta package, you do not need to specify the actual version of the package

sudo apt-get install linux-headers-386

or for Edgy:

sudo apt-get install linux-headers-generic

---

