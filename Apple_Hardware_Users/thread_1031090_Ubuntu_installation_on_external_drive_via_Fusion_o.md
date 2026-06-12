---
title: "Ubuntu installation on external drive via Fusion on a MacBook"
date: 2009-01-05
forum: Apple Hardware Users
---

### Post by Quantum Anomaly on 2009-01-05
I want to know if it is possible to install Ubuntu on an external hard drive and run in from my MacBook - AND do it through VMWare Fusion?

And how difficult is it for an Ubuntu beginner to set this up?

---

### Post by bryonak on 2009-01-05
I'm not familiar with Fusion, but what about creating a new VMWare disk image there and installing Ubuntu on it? Like you would do on your local drive, just put the path of the virtual partition to the external drive.
Obviously you can only see and boot the image as long as the drive is plugged in.

Is this what you wanted?

---

### Post by cyberdork33 on 2009-01-05
If you want to boot natively, as well as boot within Vmware fusion, then probably not. booting from an external drive requires a little voodoo with grub-efi right now.

---

### Post by morriske on 2009-01-05
Really, it'll take some trickery. In fusion you can link to a disc image anywhere, why would it be more difficult to put it on an external drive?

---

### Post by pxwpxw on 2009-01-05
> **Quantum Anomaly said:**
> I want to know if it is possible to install Ubuntu on an external hard drive and run in from my MacBook - AND do it through VMWare Fusion?

And how difficult is it for an Ubuntu beginner to set this up?

Direcrt booting depends on the MacBook model - 2,1 is good.  Otherwise using virtual sounds interesting.

---

### Post by cyberdork33 on 2009-01-06
> **morriske said:**
> Really, it'll take some trickery. In fusion you can link to a disc image anywhere, why would it be more difficult to put it on an external drive?
I am not talking about putting an image file on the external. I am talking about doing an install on an external and then accessing the install with fusion. There is a difference.

---

### Post by Quantum Anomaly on 2009-01-07
Hmmm, well as long as one method or another will work.
I just ordered an external drive from Amazon.
So... hopefully I'm not screwing myself here.

I don't need to be able to boot to Ubuntu directly. I just want to be able to run Ubuntu on my MacBook without having to use local drive space or modifying the way my Mac boots up (just because I don't want to risk messing anything up).

Of course there is a chance that the application I need to run in Ubuntu (Blender) will not perform well through a virtual machine, in which case I will need to boot directly from the drive, but I'm trying this first (fingers crossed).

---

### Post by bryonak on 2009-01-07
As far as I see it, you have the following scenarios:

1. Install Ubuntu on an external drive and select it when booting EFI (as long as your BIOS/EFI supports booting from USB, which should be fine on new Macs).
This would probably give you the best performance, since no virtualization happens.

2. Have the external drive as storage (any file system you want) and save a VMWare image there, which you can boot with Fusion from OSX.

3. Have a working Ubuntu install *and* a stored image on the drive, so you can do 1. and 2.
But then the two installs of Ubuntu are separate and can't exchange files directly.

4. do 1. and then load that existing install in Fusion (there should be an option for that), without having a virtual image.
This is the trickiest to set up and has the greatest risk of errors, but you can then use the same Ubuntu install from within OSX (with Fusion), at boot time (Ubuntu only without OSX) or on a completely different Computer.

I'm a bit sparse on links, but everything I said can be found in these forums or via Google.
Btw what hardware are you using?

---

### Post by Quantum Anomaly on 2009-01-07
> **bryonak said:**
> Btw what hardware are you using?

Black MacBook 2.4 GHz 4GB RAM 250GB HDD running OS X 10.5.6
Graphics: Intel GMA X3100
(The GMA chipset doesn't shake hands with Leopard when it comes to certain OpenGL standards which Blender utilizes. Hence the need for Ubuntu)

---

### Post by cyberdork33 on 2009-01-07
> **bryonak said:**
> 1. Install Ubuntu on an external drive and select it when booting EFI (as long as your BIOS/EFI supports booting from USB, which should be fine on new Macs).
This would probably give you the best performance, since no virtualization happens.
this does not work on most Macs (in fact there are very, very few that have reported it does work at all)

> **bryonak said:**
> 2. Have the external drive as storage (any file system you want) and save a VMWare image there, which you can boot with Fusion from OSX.
This would be my recommendation if I follow what you want. However, running in a VM will slow down Ubuntu, but running it in a VM that is reading everything over USB will be even slower...

---

### Post by bryonak on 2009-01-07
> **cyberdork33 said:**
> this does not work on most Macs (in fact there are very, very few that have reported it does work at all)


Since EFI boots from a GPT drive if possible, and GRUB doesn't install on those, this is indeed tricky.
How comes rEFIt offers me to boot from an USB stick if I have one inserted while booting?
Never tried it, but I was under the impression that this might be used to boot from a thumb drive... or for that matter USB external HDD, which isn't that different.
There were some GRUB/GRUB2 patches to support this as well, I hoped that they entered upstream, but google doesn't tell.
There's still ELiLo, which I have no experience with, but might do the trick.


> 
This would be my recommendation if I follow what you want. However, running in a VM will slow down Ubuntu, but running it in a VM that is reading everything over USB will be even slower...
Right... since he doesn't want to touch his internal drive, booting from external or liveCD is the only option. The virtual image thing makes it "simple".

---

### Post by cyberdork33 on 2009-01-08
> **bryonak said:**
> Since EFI boots from a GPT drive if possible, and GRUB doesn't install on those, this is indeed tricky.
You can boot from an external device if you boot natively from EFI... that means using GRUB-EFI (GRUB2) instead of GRUB, but there are other limitations to do that, like no 3D acceleration if you can get it to boot that way at all. pxwpxw has been working on this for awhile:
[http://ubuntuforums.org/showthread.php?t=995704](http://ubuntuforums.org/showthread.php?t=995704)

> **bryonak said:**
> How comes rEFIt offers me to boot from an USB stick if I have one inserted while booting?
Never tried it, but I was under the impression that this might be used to boot from a thumb drive... or for that matter USB external HDD, which isn't that different.Oh it will try, but it will also fail, and it is not rEFIt's fault. It is the EFI firmware that will not boot legacy operating systems from external devices

> **bryonak said:**
> There were some GRUB/GRUB2 patches to support this as well, I hoped that they entered upstream, but google doesn't tell.
There's still ELiLo, which I have no experience with, but might do the trick.yep, as mentioned. elilo has limted support too as far as I know. It works on Mac Mini's but that is about it i think.

> **bryonak said:**
> Right... since he doesn't want to touch his internal drive, booting from external or liveCD is the only option. The virtual image thing makes it "simple".
Right, and unless there is some overwhelming reason to install natively, I would stick with a VM.

---

### Post by Quantum Anomaly on 2009-01-09
> **cyberdork33 said:**
> running in a VM will slow down Ubuntu, but running it in a VM that is reading everything over USB will be even slower...

Good point you bring up. 

The other option would be keeping the Ubuntu image on my local drive and just saving all my files to the external. What would you say is the minimum amount of space I should devote to Ubuntu? Somebody told me 30GB. It would be nice if I could get away with less though since I only have 18GB free at present.

---

### Post by cyberdork33 on 2009-01-09
> **Quantum Anomaly said:**
> Good point you bring up. 

The other option would be keeping the Ubuntu image on my local drive and just saving all my files to the external. What would you say is the minimum amount of space I should devote to Ubuntu? Somebody told me 30GB. It would be nice if I could get away with less though since I only have 18GB free at present.
well, that really depends on what you plan to do with it, but I usually create my installs with an 8GB or 10GB virtual drive. (Plus these are usually "expandable" images, meaning that they won't take up 8GB of space, just the amount needed to hold the files in the image, and can expand up to 8GB if needed.)

---

### Post by Quantum Anomaly on 2009-01-09
Looking in Grand Perspective here I'm realizing that there are some large files I have that I don't necessarily need to keep on my local drive. So when my external drive is delivered I will move those files to the external and I won't feel as pressed for drive space. Then I will set up Ubuntu via Fusion. 

Also, I found this tutorial that describes how to set up Ubuntu so that your files are still stored on the Mac portion of your drive in a folder that Ubuntu can access:

[http://www.daniweb.com/forums/thread82083.html](http://www.daniweb.com/forums/thread82083.html)

Sounds like a good idea since I wouldn't have to worry about filling up the Ubuntu image. Any reasons why this would or would not be ideal?

---

### Post by Quantum Anomaly on 2009-01-09
Also, I have Time Machine set up, so having my documents on the OS X part of the drive means my important work will get backed up automatically. 

When you install Ubuntu through Fusion, is the whole virtual machine one file / disk image? Or is it a normal file folder? Because if it's all one file it would be too big to make scheduled back-ups practical.

---

### Post by cyberdork33 on 2009-01-09
> **Quantum Anomaly said:**
> Also, I have Time Machine set up, so having my documents on the OS X part of the drive means my important work will get backed up automatically. 

When you install Ubuntu through Fusion, is the whole virtual machine one file / disk image? Or is it a normal file folder? Because if it's all one file it would be too big to make scheduled back-ups practical.
the disk image is one big file. I normally tell time machine not to look in my VM folder.

---

### Post by Quantum Anomaly on 2009-01-11
I got Ubuntu installed through Fusion, but I can't figure out how to install VMWare Tools. Can anybody help, please? :confused:

Specifically what's going on is I don't see the .rpm file that's supposed to be in the VMWare Tools installer. Instead I see "manifest.txt"... I have no idea what that is, but it seems to be a script of some sort. 
Where's the file called something like "VMWareTools-e.x.p-51348.i386.rpm"? (not sure if the numbers are the same in my version)


[SIZE="1"](And thank you, cyberdork - I did just as you described with Time Capsule. Now I just gotta get my Mac/Linux shared folder operational with VMWare Tools...)[/SIZE]

---

### Post by bryonak on 2009-01-12
> **Quantum Anomaly said:**
> I got Ubuntu installed through Fusion, but I can't figure out how to install VMWare Tools. Can anybody help, please? :confused:

Specifically what's going on is I don't see the .rpm file that's supposed to be in the VMWare Tools installer. Instead I see "manifest.txt"... I have no idea what that is, but it seems to be a script of some sort. 
Where's the file called something like "VMWareTools-e.x.p-51348.i386.rpm"? (not sure if the numbers are the same in my version)


[SIZE="1"](And thank you, cyberdork - I did just as you described with Time Capsule. Now I just gotta get my Mac/Linux shared folder operational with VMWare Tools...)[/SIZE]

You have three ways of installing these:

1. Go to [VMWare's repositories]("http://packages.vmware.com/tools/esx/3.5u3/ubuntu/dists/hardy/restricted/index.html") and choose the version of Ubuntu you installed (32bit = i386, 64bit = amd64, yours is 32 I guess), then download the bottom package (vmware-tools_7...). Open it in Ubuntu and install if you can, otherwise download the additional packages it requests from the link above.

2. [Here's a tutorial]("http://ubuntu-tutorials.com/2008/06/07/how-to-install-vmware-tools-on-ubuntu-804-guests/") on the old and proven way. It's written for 8.04, but the instructions are the same for 8.10.

3: Convert the .rpm to a .deb with alien. More on that:

There are two big packaging systems in the Linux world: APT and RPM.
APT (advanced packaging tool) is used by Debian and it's derivatives (for example Ubuntu, Knoppix or Xandros) and the extension is .deb.
RPM (RedHat package manager) is used by RedHat and it's derivatives, as well as Suse and Mandriva.

You can convert .deb <-> .rpm with a command line tool called alien, though there are packages where it doesn't work because of the not-completely-overlapping feature sets of those systems.
There are also other less widespread ones like Gentoo's Portage (quite similar to APT) or Arch's Pacman.

---

### Post by Quantum Anomaly on 2009-01-14
Thanks, Bryonak!

After some confusion I finally got VMWare Tools installed. So now where will the shared folder that I created show up in Ubuntu?

Thanks

[EDIT]
Nevermind, I got it. It's "\mnt\hgfs\"

Now if I can figure out how to make a shortcut to this on my Ubuntu desktop, I will be all set.

---

### Post by Quantum Anomaly on 2009-01-14
Never did figure out how to make the shortcut - I guess I need to make a "launcher", but launchers only seem to work for applications. Whatever... I added it to my "Places". Close enough for now.

I have a bigger problem at the moment. 
I found I cannot yet write to my shared folder, so I tried to enable sharing and was told to install something and then restart Ubuntu. Did that. Then I got this "error 255":
[IMG]http://www.quantumanomaly.com/hostedcontent/Ubuntu_Folder_Sharing_Error.png[/IMG]

What does this mean?

I tried enabling sharing from the OS X side, but that didn't seem to make a difference. Please help!

---

### Post by cyberdork33 on 2009-01-15
> **Quantum Anomaly said:**
> What does this mean?
because of the way it was mounted, you do not have permission to share the folder (your Ubuntu user does not own it).

You are starting to deal with some of the intricacies of working within a VM that are usually specific to whatever VM you are using. You will probably find more help at the website for the VM software you are using.

---

### Post by Quantum Anomaly on 2009-01-15
I see - thank you.

I have a support request in to VMware. Hopefully they'll get back to me on Monday. 

I'm almost out of the woods.

---

### Post by cyberdork33 on 2009-01-16
> **Quantum Anomaly said:**
> I see - thank you.

I have a support request in to VMware. Hopefully they'll get back to me on Monday. 

I'm almost out of the woods.
VMWare has a forum:
[http://communities.vmware.com/community/vmtn/desktop/fusion;jsessionid=77F3B1294A73298202C85E3A8AD305E1](http://communities.vmware.com/community/vmtn/desktop/fusion;jsessionid=77F3B1294A73298202C85E3A8AD305E1)

---

### Post by Quantum Anomaly on 2009-01-16
VMware support got back to me and provided me with the solution. Here are their instructions:

[COLOR="DarkGreen"]1.open terminal and type the following command.

   [FONT="Courier New"]sudo gedit /etc/samba/smb.conf[/FONT]

2.Enter your user account password when it prompts.
 (note:the password which you enter will not be displayed on the screen).

3. It opens a text file in which you can find  " [FONT="Courier New"][global][/FONT] " below that in a new line type " [FONT="Courier New"]usershare owner only = False[/FONT] " and save the
  file.

4. Close the window.

5. Restart Ubuntu.

6. Try to access shared folder.[/COLOR]

So once you do those steps you can go to the folder properties within Ubuntu and click the checkboxes that designate it as a shared folder. This worked perfectly for me. Now every file I create in Ubuntu that I want to be accessible from OS X, I can simply save to my shared folder. And once it's there it will be backed up by Time Machine on my OS X side. :P

---

