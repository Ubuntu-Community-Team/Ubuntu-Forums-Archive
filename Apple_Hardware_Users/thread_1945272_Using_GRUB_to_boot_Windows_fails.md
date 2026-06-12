---
title: "Using GRUB to boot Windows fails"
date: 2012-03-22
forum: Apple Hardware Users
---

### Post by Mk32 on 2012-03-22
A common problem, I know, but nobody seems to have a clear cut solution.

I don't want rEFIt. It doesn't work right on my quad-boot setup since when I installed grub on /dev/sda5/ it wouldn't boot Linux right. 

....Anyways. The setup:

Mac Mini 1,1 2.16GHz CD
/dev/sda2/: Leopard (10.5.8)
/dev/sda3/: Tiger (10.4.11)
/dev/sda4/: Windows XP SP3
/dev/sda5/: 9.10 Ubuntu

I have no problem going through two bootloaders to boot either Linux or Windows. What I do have a problem with is that Windows being selected doesn't boot Windows. GRUB is installed on /dev/sda4/. Installing GRUB on /dev/sda5/ means that the partition can be seen from the EFI and rEFIt, but will never work. 

So what do I have to type or do in GRUB/Linux to get Windows working?

Not to mention, I have yet to install the swap partition...

---

### Post by Mk32 on 2012-03-25
I am astonied by the lack of responses...maybe my problem is too complicated?

I am using 9.10, I don't know if it is using grub2 or grub legacy. I just used the Windows XP disc to fix the MBR using the recovery console so at least I can still blast bots in CounterStrike. 

I have no problem reinstalling Ubuntu again, but the way it is going is not encouraging. I would like to check out that certain video editor (doesn't help that all the entries in the Software Center say "Not available in e current data"  and running sudo apt-get update doesn't work) and fiddle with Netatalk.

---

### Post by Mk32 on 2012-03-29
I **will** stick at this until it will work. 

I [followed this tutorial]("http://www.dedoimedo.com/computers/grub-2.html") as best as I could, and did the following...

1. Open gedit. Entered in the relevant text, I'll have to reboot in Ubuntu to see what I typed. 
2. Save said document on desktop. Opened Terminal. 
3. Navigated to /etc/grub.d/
4. Entered: "$ sudo cp '[whatever the path to the desktop was]/41_windows_xp' /etc/grub.d/
5. It copied. Then I typed "$ chmod +x 41_windows_xp
6. "$ sudo update-grub"

Rebooted, the menu option was there, but selecting the (regular) Windows install does nothing but a black screen for a second, then returns me to GRUB 2 menu. Selected the "testing" version gives me an error: "Error: two arguments needed"

I also have that retarded error in Software Center about not being in the current data. I did run "$ sudo update-get" or whatever and it gives a lot of 404s. So I'll be in for a bit...):P

---

### Post by Mk32 on 2012-04-01
Here is an image of attempting to load the repositories: 

[IMG]http://i26.photobucket.com/albums/c113/Starofire/Random/955316de.png[/IMG]

As I am at the moment incapable of pleasing both children (XP and Ubuntu) in the same playpen, I just settled for an emulator. (This exact same thing happened when I did have Ubuntu working normally, but then I couldn't use XP.)

Tried sudo apt-get update, you can see the results in the Terminal window, tried checking all 325 USA sources, and nothing has come of it except 404s.

---

### Post by marinara on 2012-04-01
see [http://askubuntu.com/questions/93310/updating-karmic](http://askubuntu.com/questions/93310/updating-karmic)

---

### Post by Mk32 on 2012-04-01
Well...that's a rush...

No more repository listings, such as for PiTiVi, which is the 2nd reason I'm even installing Linux...

[From what I see here,](http://packages.ubuntu.com/search?keywords=PiTiVi&searchon=names&suite=all&section=all) it isn't even listed. Wonder why?

Only reason I chose 9.10 was because it had GNOME 2, I don't like GNOME 3, or Unity. 

I'll go ahead and download 10.04. How do I change the color theme back to the old style orangish-brown? I liked GNOME that way.

---

### Post by mode7 on 2012-04-02
> I don't want rEFIt. It doesn't work right on my quad-boot setup since when I installed grub on /dev/sda5/ it wouldn't boot Linux right. 
Just curious, did you fix the hybrid mbr after installing grub? I need to use gdisk from OSX each time I install Ubuntu ([http://ubuntuforums.org/showpost.php?p=11215214](http://ubuntuforums.org/showpost.php?p=11215214)), otherwise grub gives me a 'missing operating system' error after I select Ubuntu from refit. Instructions are for MBA, but works fine on my MBP 8,1.

I wish I could help with Windows, but I haven't tackled triple booting on here yet..

Edit: Btw, if you want to stick with Gnome 2, or something similar, I recommend you use an up-to-date Ubuntu, but with XFCE, or perhaps pulling MATE from Linux Mint repos.

---

### Post by Mk32 on 2012-04-02
I couldn't. 

I spend the total part of about 72 hours trying different things to make it work. I wanted four operating systems as described in the first post. I just don't get why others can do it...one popular guide used Leopard, XP, Vista and Ubuntu.

Now Vista's mediocrity is well known, but one commenter on that guide said he just put Tiger last and skipped Vista. Didn't work for me. 

The fundamental problem is GRUB wants a MBR slice, and XP wants its own too, and selecting between them is a challenge that neither can solve. You could do it the hard way, reinstalling GRUB after each time you have finished with XP, and then you'd have to use the Recovery Mode and *fixmbr* and *fixboot* to restore Windows. Non-optimal...

I don't know anything about "XCFE" or "MATE"...my techie knowledge isn't THAT high yet. 

But as it is what it is, I just settled on using VirtualBox under 10.5 (which I don't like 10.5) to get me buy. I'm only pulling up Ubuntu for a couple of reasons: 1) test out PiTiVi, 2) work on a tutorial for networking classic Macs with NetaTalk, and 3) fiddle with Adanaxis again. 

It hurts a bit, I really do like the orangish-brown hues that I first experienced on a Compaq E500 with Ubuntu 7.10. (Of course that and 9.04 on another laptop had some *serious* issues, but that's another story.)

EDIT: I didn't use gdisk, when I worked without XP (even though it was installed and I could see its logical blocks from Partition Inspector) I would boot Linux from EFI. It says "Windows" but ignore it. 

I'd be perfectly happy chainloading XP from the GRUB menu, using EFI to select Windows, which loads GRUB, from there I'd select either Windows or Ubuntu. While I like rEFIt, I'd rather have something that at least _works_ rather than doesn't work.

---

### Post by mode7 on 2012-04-03
Well, I don't consider myself software illiterate.. but when it comes to bios/efi/bootloaders/ETC, I am pretty clueless and get headaches easily. Which does not help with my Macbook and the fact that I may want Lion/Ubuntu *and* Windows in the near future. Ubuntu and Lion works fine, though, so I may change nothing for a while.

Depending on how much you want to use Ubuntu on your Mac (You said you wanted to do some testing), you may try methods of getting Just Tiger/Leopard/XP to boot successfully, then boot Ubuntu from inside Windows using Wubi. 
Don't ask me specifically how, perhaps trying Refit again or using Boot Camp will work, but idk how Boot Camp behaves with Tiger on there..
There are also some other EFI bootloaders like elilo. And of course virtualization, like you said. 

XFCE and Mate are desktop environments, like Gnome is.
XFCE is GTK-based, like Gnome, and is under active development. It's very speedy, and looks pretty nice IMO, especially under Xubuntu.
Mate is a fork of Gnome 2.. so about the closest to your Gnome 2 you can get.. however, you need to add repositories to install it, and I've not used it enough to say how stable or feature-complete it is. ([http://mate-desktop.org/](http://mate-desktop.org/))

I don't like Gnome 3 either, but Unity works great for me (Unity is just a shell over Gnome 3, btw). I'd pick XFCE second.
You can also try LXDE and KDE, although I've had issues with lxde in the past, and KDE may be too radically different for you. Give them a try, though!

---

### Post by Mk32 on 2012-04-03
[homer]All this computer hacking is making me thirsty. I think I'll order a tab.[/homer]

I have never tried anything else besides 7.10, 9.04, 9.10 and I did get a chance to fiddle with Xubuntu a bit and didn't like it. I liked GNOME 2 better, although they look a lot alike. 

I am back to the former 10.4, 10.5 and XP, because those are the ones I use. 

Boot Camp. Boot Camp is just a application that allows hot-partitioning of a HFS+ single partition into other partitions to prepare for installing Windows. That's it. You can install XP or whatever straight with no Mac OS partitions at all. If you already prepped the partitions the way you like through Disk Utility, then you don't need BootCamp entirely. You do need the drivers for XP/Vista that come on the DVD though. 

The actual booting of Windows (or GRUB) is all done through the hybrid MBR: the EFI boots the GPT (GUID Partition Table) *or* the MBR. In essence there are two bootloaders. It's a workable, but somewhat kludgy solution because the MBR can only fit four slots, one is already occupied by the EFI Protective Partition, one by OS X, and then there's two left. Not enough. 

Burnt a 10.04 CD, I'll use VirtualBox to play with it. Probably won't last very long....

---

### Post by Mk32 on 2012-04-04
Well it didn't last long. 

10.04 is so ugly and tacky I never want to use it again. I'll even discard the CD I burnt the .iso to. 

I'll need some sort of native booting for my testing. The emulator doesn't cover all bases, neither does it work so hot with USB devices. 

This all confirms why I say Windows and Linux (and many others) are not operating systems for the casual user -- they're advanced or even expert grade software. No casual user should be expected to have to compile binaries or wade through "Download this, do this, download this to run that, make a text document and chmod it, blah blah blah Oh and you'll have to launch it in Terminal using ./ to boot it, because it is a Terminal only program" just to make software work. 

Not to disrespect the work, countless hours put into a decent OS, but I think I'll stick with Mac OS X (10.4 that is) for as long as I possibly can. Everything else comes with a big blivet of refuse. 

However, because I need to work out a simple guide (for the rest of us) how to set up Netatalk, I will persevere to complete it, but I don't think I will maintain warm fuzzy memories. (However, if only Windows Vista and up (W8 excepted) looked like GNOME 2 under 9.10 and earlier...I'd snap it up without a second thought.)

---

