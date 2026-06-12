---
title: "LTSP - PowerPC - DHCP Failing?"
date: 2011-10-06
forum: Apple Hardware Users
---

### Post by Roasted on 2011-10-06
So I'm trying to set up an LTSP lab. I have a PowerPC Ubuntu "server" running as a test drive. Based on what the developers said, they believe my DHCP config is wrong, because I have the proper tftp files and such.

I simply copied my config from the example page at the bottom here:

[https://help.ubuntu.com/community/UbuntuLTSP/LTSPCrossArchSetup](https://help.ubuntu.com/community/UbuntuLTSP/LTSPCrossArchSetup)

I'm using a 192.168.100.X IP scheme in my testing grounds. But what else is there that I may be missing? 

My goal is to use PowerPC systems as the DHCP clients that are pulling from this server. Currently the PowerPC clients just fail to network boot and continue on past it.

What am I missing??

---

### Post by svtguy88 on 2011-10-06
I'm new to network booting, but your post caught my attention.  Out of curiosity, what disto/version are you using on the clients?

Anything helpful in any logs?  

I wish I had my PowerPC box up and running still.  I just upgraded to an Intel Xeon rig.  I was actually intending on setting up my PowerMac as a router, but the PCI card I bought wouldn't work in the old machine, so now the G4 just sits.

---

### Post by Roasted on 2011-10-06
I'm using Ubuntu 10.04 PPC edition on both systems.

I'd like to think I can run 12.04 PPC when it comes out but I'm not sure. We would definitely utilize it with the XFCE desktop as we currently do for our Linux systems due to the lighter frame since these systems clearly wouldn't handle a 3D oriented interface such as Unity or Gnome 3.

While I know that Ubuntu PPC is community driven at this point, so far it has proven to work decently on the G4 system I'm prepping it on.

Here's my intention:

Using the G4, install 10.04.
Using the G4, install LTSP.
Using the G4, generate a PPC chroot (only possible on a PPC system).
Using a Dell Intel based server, install 10.04.
Using a Dell Intel based server, copy the PPC's chroot to /opt/ltsp/powerpc.
/opt/ltsp/powerpc is the directory that the clients utilize as their desktop environment when they fire up via network boot. That said, it would allow me to run a mixed architecture - A 64 bit Intel based server with a ton of RAM to handle mass clients as well as the PPC chroot that the end user system will be utilizing for basic operating system functions.

As of now, everything works, however to get it working at full potential the clients clearly need to network boot. That's where it's hanging up, because within the DHCP file you can see there are some added entries regarding LTSP so the clients know which directory to pull the OS files from. That's where they find out, oh, /opt/ltsp/powerpc = where I need to look for the files to finish the startup process.

However, as I said, something is borked, as the clients are not receiving proper boot instructions.

I feel like I'm close. I'm trying not to get my hopes up, but if we can make PPC systems work we can save a ton of time and money with utilizing this still-functional hardware for the benefit of students.

---

### Post by svtguy88 on 2011-10-06
It's got to be possible.  I just don't have the necessary netboot experience to help.  I'm certainly interested though...I'll keep checking this thread.  How many netboot clients are you looking to support?  What are their specs?  I'm just curious, again.

That said, instead of using Gnome, you could install XFCE over Ubuntu and use that as your window manager.  Gnome seems like it'd be a bit heavy for all but the most beastly PPC machines (even on my dual 1.8 ghz G4 I usually used something other than Gnome).

---

### Post by Roasted on 2011-10-07
> **pkmgarf said:**
> It's got to be possible.  I just don't have the necessary netboot experience to help.  I'm certainly interested though...I'll keep checking this thread.  How many netboot clients are you looking to support?  What are their specs?  I'm just curious, again.

That said, instead of using Gnome, you could install XFCE over Ubuntu and use that as your window manager.  Gnome seems like it'd be a bit heavy for all but the most beastly PPC machines (even on my dual 1.8 ghz G4 I usually used something other than Gnome).

XFCE + Ubuntu is already the path chosen when it comes to Linux integration with the district. Mostly because XFCE is light, which is a plus, but it's also very configurable so we can spin off our own "theme" tailored just for the users, which in our case are students. Granted this is true for Gnome and KDE as well, but KDE naturally struck out considering we're dealing with older hardware, and Gnome we weren't too sure about. The desktop environment decision was made before I began working here, which was back when Unity was first announced and nobody knew how Unity vs Gnome would pan out. Considering that's all well and good now, it still doesn't change the strategy because... while Gnome 3 runs sickeningly fast on my Atom netbook, I don't think it's wise to push that kind of desktop environment through a thin client to systems as old as what we're dealing with. Ehh...

Currently we are a Mac district moving to Linux as the months pass and systems age and get replaced. I don't see a very heavy Mac future here however, Macs will always exist, likely on teacher systems especially for quite some time. Student systems, however, are full bore Linux for right now.

The count? I have no idea. We need to bench this small scale, so we'll likely take one guinea pig library and fire them up on about 20 systems and see how it goes.

Most of these systems are iBook G3/G4 or eMac G4's. The lowest specs I think I saw was 800mhz 384mb RAM. Should be plenty for an instance of a Linux desktop.

Depending on how the bench test goes, if this cross-architecture setup proves to be as reliable as the regular LTSP we all know and love, it's likely to spread like wild fire. Considering all of our labs are running older Macs, we have nothing to lose but everything to gain by making LTSP work with our PPC systems.

---

### Post by Roasted on 2011-10-10
Ultimately I ended up getting this working, but not predictably. Something told me to just reboot the server and make sure it worked. Beyond that, it was giving me hassles.

Basically the distributed "yaboot" file has issues with it. Yaboot is the "Grub" of PPC systems. I came across a bug report where a user listed the bug with exactly what was wrong. Later in the report he listed he was "tired of waiting when he put what to do right there" and uploaded his own variant of yaboot. To my surprise, it worked! 

However, it seems as if I'm having some TFTP issues at this point. On Friday I booted up and waited for it forever and it ultimately let me netboot my iBook client off of the system, but it makes no sense why it wouldn't boot right away.

Also, I noticed that some files were in proper locations. For example, within /var/lib/tftpboot/ltsp where's a "powerpc" folder where the contents are. But if you look in the DHCP config file, there are some paths corresponding where it needs certain files to be. All of my files were located improperly. However, the catch is *some* of the files had to stay. My fix? Copied the entire contents, and pasted it.

That way:

/var/lib/tftpboot/ltsp/powerpc/
/var/lib/tftpboot/ltsp/

had the same contents. Between that and replacing Yaboot, we got it working, but like I said, it's still giving me a severe headache. 

On top of that, even after updating the SSHKeys, I STILL cannot log into the system with a local account. So currently I have two issues. TFTP is being stubborn and logging in is still giving me some trouble.

Once those two things are resolved it's just a matter of rebooting several times to make sure things stick.

Ugh... PowerPC is a royal headache...

---

