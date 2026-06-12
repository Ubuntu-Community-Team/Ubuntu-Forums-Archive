---
title: "Configuring Xfce, resolution and a better apt-get repository?"
date: 2007-03-15
forum: Apple Intel Users
---

### Post by Winterhart on 2007-03-15
I'm new to Ubuntu and all that implies, although I've been running various distros on my desktops for years.  So, have a couple of (probably incredibly noobish) questions --

I have Xubuntu 6.10 installed and running on a new Mactel (MacBook Pro, actually).  It boots, and it runs (which is more than I could say for Debian), but... for running Xfce, it's astoundingly sluggish.  Windows jerk around the screen when I move them, and window content does not scroll smoothly - it behaves like a computer with nowhere near enough memory would, moving big chunks of web pages at a time.  I find it difficult to believe that a system with 2gb of RAM would be having physical memory issues, so I must have something configured inefficiently.
Someone suggested to me that I look into 'compositing', but there's no mention of such an option in any of the Window Manager Tweaks/Preferences/etc dialogs which are presented in the settings menu.  (EDIT:  I'll be trying [this]("http://ubuntuforums.org/showthread.php?t=343488") when I get home today, so for now ignore this paragraph!)

I am also not convinced that it is running at the correct resolution - the only entry for 24bit color in Xorg.conf is "1440x900", but if that's correct it's really small - a terminal window takes up literally 3/4 of the screen, and (from memory) I can get maybe 2 dozen lines of text displayed in that terminal.  In short, it looks like I'm running at 800x600 on a normal monitor.  Wikipedia said that 1440x900 is the default for a 15" MBP, but... sanity check, please?

Last but not least, I am trying to adjust to a package-managed distro (and oh, it's tough!).  There's a thread [here]("http://ubuntuforums.org/showthread.php?p=1646311") discussing pypanel, and the OP mentions having gotten it from an Ubuntu universal repository - I tried 'apt-get install pypanel', and it couldn't find anything by that name.  Does anybody know where that repository is?  Are there web interfaces for any of these repositories?

Thanks for your patience!

---

### Post by shrini on 2007-03-15
You can try **[Envy]("http://albertomilone.com/nvidia_scripts1.html")** install to install proprietary ATI drivers to get full resolution. I had the same problem for my 17" mbp would not run in native resolution. But after running the Envy script it runs in full 1680x1050 resolution. Best of all the entire install is automated and even tweaks the xorg.conf for you.

I spent multiple nights trying to get the xorg.conf settings to get full resolution till I came across this install package. 

Now I am struggling with Beryl.

Hope this helps

---

### Post by Winterhart on 2007-03-15
I honestly have nothing to say except thank you, many times over!   I did the 'apt-get -f install' that I should have done right after I did the initial install, installed Envy, and then Envy took it from there.  This thing looks absolutely beautiful now (I have screen real estate! :o)  and the problems with moving windows, scrolling, etc are gone.

Also, I figured out the universal repository thing - the lines were just commented out in my sources.list file.

On to see whether the new repository can help out with the pypanel issue - again, thanks!

---

