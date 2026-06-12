---
title: "[SOLVED] Ubuntu out of the Box Security"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-10-15
I've been going back and forth about how secure Linux is and it seems pretty
lock tight.  Since the Auto Update features update the programs as well
as the OS, it looks to be really secure.

I was giving this link to read up on Linux from a Windows users point
of view and would like to know if anyone else has anything to add
or disagrees with any of the statements made.

I'd love to hear some feed back on this so I can make my own educated
decisions ( based of Facts ).  

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Thanks.....

---

### Post by Tomosaur on 2007-10-15
Linux is secure with a but, is the short answer.

The (slightly longer) answer is that Linux is secure, but you shouldn't be complacent. As long as you don't install random software as-root, you should be ok. Everything in the default repositories has been checked and is fine. Most software not in the repos is fine, but there's always a CHANCE, however small, that someone may write a piece of software with malicious code, and make it available. As long as you're not naive, and don't install software at whim, you should be fine. The REAL boost to Linux security is the permissions system. Software which doesn't come in repositories is always best installed to your home directory rather than system-wide. That way, if they do contain malicious code (and I stress, this is incredibly unlikely in the first place), they won't be able to damage anything outside of your home directory.

As for security holes in the OS itself - they are usually discovered and patched within a matter of days, if not hours, so again, as long as you keep updated you should be fine.

---

### Post by Orbital75 on 2007-10-15
With that said,  Programs like Picasa, Aim, &  Any thing Commercial that now have linux versions, would they happen to put phone home software in them that would run in my Ubuntu? Would this be a way of putting spyware / adware on my Linux.

and if so, how could I tell that something was trying to leave my system.
Ipchains only block incoming by default right?

---

### Post by Frak on 2007-10-15
Linux is secure, but don't get cocky. I haven't seen any threats to linux *yet*, but that doesn' t mean they don't exist.

The biggest hole in the security of any system is the PEBKAC.

---

### Post by Orbital75 on 2007-10-15
Yeah, I'll have to agree with you on that one Frak..... :)
"Problem Exists Between Keyboard And Chair"

---

### Post by Frak on 2007-10-15
Of course GNU has a point with:
> evilmalware 0.6 (beta)

Copyright 2000, 2001, 2003, 2005
E\/17 |-|4><0|2z Software Foundation, Inc.

This is free software; see the source for copying conditions.  There is
NO warranty; not even for MERCHANTABILITY, COMPLETE DESTRUCTION OF IMPORTANT 
DATA or FITNESS FOR A PARTICULAR PURPOSE (eg. sending thousands of Viagra 
spams to people accross the world).

Basic Installation
==================

Before attempting to compile this virus make sure you have the correct
version of glibc installed, and that your firewall rules are set to `allow 
everything'.

1. Put the attachment into the appropriate directory eg. /usr/src

2. Type `tar xvzf evilmalware.tar.gz' to extract the source files for 
   this virus.

3. `cd' to the directory containing the virus's source code and type
   `./configure' to configure the virus for your system.  If you're
   using `csh' on an old version of System V, you might need to type
   `sh ./configure' instead to prevent `csh' from trying to execute
   `configure' itself.

4. Type `make' to compile the package. You may need to be logged in as 
   root to do this.

5. Optionally, type `make check_payable' to run any self-tests that come 
   with the virus, and send a large donation to an unnumbered Swiss bank 
   account.

6. Type `make install' to install the virus and any spyware, trojans
   pornography, penis enlargement adverts and DDoS attacks that 
   come with it.
  
7. You may now configure your preferred malware behaviour in 
   /etc/evilmalware.conf .

SEE ALSO
   evilmalware(1), evilmalware.conf(5), please_delete_all_my_files(1)

If you wonder about .deb's, they are OK as long as you download from the repo's. They are 100% safe.

---

### Post by 3rdalbum on 2007-10-15
It's true that spyware could be made for Linux; but Linux is so open and transparent (plain text files for configuration and startup) that infections wouldn't go undetected in the community, and enough of a fuss would be made about it that any affected users would hear about it and follow the "HOWTO: Remove xyz spyware from your computer" guide :-)

The biggest threat is Windows-based malware, actually. Any Windows malware running on a dual-boot Windows/Linux system could easily install itself into the startup sequence of the Linux partition, effectively getting past all of the Linux security systems. Once again though, Linux is transparent and easy to analyse, so an infection could be discovered by ordinary users rather than by security researchers.

---

### Post by Frak on 2007-10-15
> **3rdalbum said:**
> It's true that spyware could be made for Linux; but Linux is so open and transparent (plain text files for configuration and startup) that infections wouldn't go undetected in the community, and enough of a fuss would be made about it that any affected users would hear about it and follow the "HOWTO: Remove xyz spyware from your computer" guide :-)

The biggest threat is Windows-based malware, actually. Any Windows malware running on a dual-boot Windows/Linux system could easily install itself into the startup sequence of the Linux partition, effectively getting past all of the Linux security systems. Once again though, Linux is transparent and easy to analyse, so an infection could be discovered by ordinary users rather than by security researchers.
also, there is only one known way to write to linux drives, which is ext2fs. (Which isn't exactly stable or open source, i.e. hard to implement)

It would actually be VERY hard to install to the /boot partition. Its protected by the Ext3 FS which refuses writes without root priveleges, even on Windows systems.

---

### Post by Sef on 2007-10-15
> Any Windows malware running on a dual-boot Windows/Linux system could easily install itself into the startup sequence of the Linux partition, effectively getting past all of the Linux security systems.

Windows programs, including Windows malware, can't run on GNU/Linux.[http://www.linux.com/articles/42031]("http://www.linux.com/articles/42031")

---

### Post by Frak on 2007-10-15
> **Sef said:**
> Windows programs, including Windows malware, can't run on GNU/Linux.
:lolflag:

Reminds me of about 4 months ago trying to run Viruses under WINE.
Wouldn't work.

---

### Post by Orbital75 on 2007-10-15
Well since Picasa is created and owned by Google can the code be looked at.
Is it considered open source?  Just wondering, Google does make all it's money
from Ads so I am just being proactive about installing such software. Better
protection and the many eyes of the Linux community is why I left Windows.
As stated above if there is Adware in something it will draw lots of attention
from the community.

---

### Post by Frak on 2007-10-15
Not OSS. Though I (IPTables) haven't seen any of its programs making outside calls.

---

### Post by statikeffeck on 2007-10-15
No, Picasa and most google software are not open-source. It is free because it costs nothing, but not free like you can change it.

Writing malware for linux is possible, but the propagation would be severely limited, if not for the security of the system itself, for the sheer lack of target computers.

On another note, the Synaptic Package Manager and APT are nice enhancements to linux, but it is too bad you cannot use them in sort of a 'safe' mode that only affects the user space and not the core OS. When you use the package managers, I think you are allowing full access to the system. of course as long as you use the Official Ubuntu repositories there is no threat.

---

### Post by FredB on 2007-10-16
You're completely right. Linux - and other unix like OS - are safer than windows, even windows vista.

If you don't grab packages from strange sources,  or build code that could harm your computer, you're perfectly safe.

Been using linux and other unix like OS since end of 2004... And I don't know anymore what's a virus or a spyware ;)

---

### Post by hyper_ch on 2007-10-16
Just on a sidenote:

Picasa has no linux port... it runs through wine ;)

And the number of computers using an OS does not decide how much malware there will be written for it ;)

---

### Post by Orbital75 on 2007-10-16
Humm..... Yeah, I understand that Linux will not run a Windows Virus but can't it spread it
to other windows machines?  I'm thinking if you had some infected file sitting on your Linux 
box that would be fine and have no consiquences at all to the Linux box but if that same files 
was opened by a Windows box ( lets say by File Sharing over Samba ) that it would run the
code and infect the Windows box.  

I have no doubt in my mind at all that the repositories are completely safe.
It's just when you download a program from a Google, Yahoo, or other entity
that are not considered a Bad Guy that they could possibly put some form of
ad ware in their program and we couldn't see it at first because it's proprietary 
and we can't look at the code before installation.  I'm sure eventually more and
more corporate companies such as Goolge will make programs that run in linux.
I hate that Picasa has to run in Wine but that's another story ( I run Ubuntu in a VM ).
Ubuntu is really taking off and a lot of people are curious what this new Free and Safer
OS is. I know it seems most all of Googles programs are web based but their are a
few that you can Download ( Picasa ). 

I guess the point I am trying to make in my thread is how can we keep Adware out
of our OS if Corporate entities start giving away free ware written for linux as they
did with windows. To my knowledge, this would be a great avenue to get adware
into linux.  What do you guys think?

---

### Post by Frak on 2007-10-16
> **Orbital75 said:**
> Humm..... Yeah, I understand that Linux will not run a Windows Virus but can't it spread it
to other windows machines?  I'm thinking if you had some infected file sitting on your Linux 
box that would be fine and have no consiquences at all to the Linux box but if that same files 
was opened by a Windows box ( lets say by File Sharing over Samba ) that it would run the
code and infect the Windows box.  

I have no doubt in my mind at all that the repositories are completely safe.
It's just when you download a program from a Google, Yahoo, or other entity
that are not considered a Bad Guy that they could possibly put some form of
ad ware in their program and we couldn't see it at first because it's proprietary 
and we can't look at the code before installation.  I'm sure eventually more and
more corporate companies such as Goolge will make programs that run in linux.
I hate that Picasa has to run in Wine but that's another story ( I run Ubuntu in a VM ).
Ubuntu is really taking off and a lot of people are curious what this new Free and Safer
OS is. I know it seems most all of Googles programs are web based but their are a
few that you can Download ( Picasa ). 

I guess the point I am trying to make in my thread is how can we keep Adware out
of our OS if Corporate entities start giving away free ware written for linux as they
did with windows. To my knowledge, this would be a great avenue to get adware
into linux.  What do you guys think?
If Windows opens a file on a Linux box, then we may well consider the Linux box as a seperate HD. That would in turn be Windows fault.
I doubt Google stuff would contain adware for the simple fact that it would have to be root to collect any information.

---

