---
title: "I...I can't install a new program! There I said it"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by icelechi on 2006-07-08
OK, I do not know how to install a new program. Most downloaded programs come with the same list of files: INSTALL, install-sh, configure.in, etc. What do you do to install the new program. I have tried typing **./configure**, then ** make **, then ** make install **. But that does nothing.

Any one know what to do?

---

### Post by Iarwain ben-adar on 2006-07-08
Hi,
First of all, welcome to the forum ;)
Tell me please, what program is it?

And could you tell us what kind of file it is you have downloaded? 
Is it a .deb, a folder, etc.


Iarwain

---

### Post by Apple 101 on 2006-07-08
What files does it come with? configure? install-sh? autogen.sh?  What programme are you trying to install?  Generally, use ./configure (make and then sudo <password> make install), ./autogen.sh.

It could be in the repositories, so enable Universe and Multiverse (optional) in Synaptic and select Reload.  Then, just search for what you want.

---

### Post by PriceChild on 2006-07-08
People new to ubuntu really shouldn't be forced into compiling immediately.

I suggest you open up the synaptic package manager.

((System>Administration>Synaptic)) - or something similar

In here, you can view all the official supported software around for ubuntu.

When comfortable with that, you can enable more repositories, then maybe compiling :P

---

### Post by Jax Kovak on 2006-07-08
I agree with you PriceChild, but I have a very similar problem with some software that is not available in the synaptic package manager.

Just today I downloaded GNU ASpell for Firefox/Opera, but it came as an archive. I unpacked that into a folder and tried to follow directions which started with "./configure" etc, but these commands fail.

I am also a newbie, with no fear whatsoever of using the command line, but I have no idea what to do when commands given in the installation instructions fail!

I had a very similar problem with a program called ComputerTemperatureMonitor. That actually came as a deb file, which Ubuntu duly installed for me. However, it did not create any menu items for the program and typing the name of the program has no effect.

In fact, having searched for the program I found it as a series of script files in the Python folder in /usr/lib, however, the instructions, such as they are, give commands which fail straight away. For example the 'make' and './configure' commands are not found at all, in any installation I have tried.

Any tips about this sort of thing would be gratefully received because I can see that otherwise I will end up with an Ubuntu installation that gathers dust because I cant install anything new!

Jax

---

### Post by DSn0wMan on 2006-07-08
@ Jax

The nuber one reason "./configure" fails is missing dependencies. 

Please post your error messages so someone can help.

---

### Post by aysiu on 2006-07-08
GNU Aspell is in the repositories: > Package aspell

    * warty (text): GNU Aspell spell-checker
      0.50.5-3: all
    * hoary (text): GNU Aspell spell-checker
      0.50.5-5: all
    * breezy (text): GNU Aspell spell-checker
      0.60.3-5: amd64 i386 powerpc
    * dapper (text): GNU Aspell spell-checker
      0.60.4-2: amd64 i386 powerpc
    * edgy (text): GNU Aspell spell-checker
      0.60.4-4: amd64 i386 powerpc Just do ```
sudo aptitude update
sudo aptitude install aspell
``` Read more here: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Jax Kovak on 2006-07-08
Thanks guys, Ill check ASpell and check dependencies on the monitor program later - Just running out the door!

Jax

---

### Post by t0rment2004 on 2006-07-08
I have a problem simular to this guys. You see, I installed today and this is my first Linux. I have no idea how to install programs, or if it's even possible. I would really appreciate it, as I don't have anything on here that isn't factory. I need to get stuff like Flash and Java if I ever hope of using this OS to its full potential. I also am a musician and I wish to try the Linux MultiMedia Studio, but because I have used Windows for years I have no idea how to install on Linux. Again, sorry for being a gigantic n00b, but I really need the help. So, just tell me in very general terms how to install programs. Thank you.

---

### Post by aysiu on 2006-07-08
These two guides explain a bit about the major ways to install programs in Ubuntu:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

You may also, since stuff like Flash and Java is important to you, want to look into some installation scripts like Easy Ubuntu, BUMPS, or Automatix. You can read more about them [here](http://www.ubuntuforums.org/showthread.php?t=185643).

For Linux Multimedia Studio, just [make sure you have extra repositories enabled](http://www.psychocats.net/ubuntu/sources), and then paste this command into the terminal: ```
sudo aptitude update && sudo aptitude install lmms
```

Take it slow and ask a lot of (specific) questions.

---

### Post by PriceChild on 2006-07-08
If you still want to compile apps... Make sure you've installed the basic compilers:

```
sudo apt-get install build-essential
```

---

### Post by John.Michael.Kane on 2006-07-08
[**[COLOR="Red"]Build-essential installed by default[/COLOR]**]("http://www.ubuntuforums.org/showthread.php?t=192840&page=7") theres seems to be some talk of it being security risk.if this is true or not is unknown.

---

### Post by icelechi on 2006-07-08
> **DSn0wMan said:**
> @ Jax

The nuber one reason "./configure" fails is missing dependencies. 

Please post your error messages so someone can help.


Hi,
I am trying to install gtkpod and when I tried ./configure, this was the message that was printed:

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

Any idea what this all means?

---

### Post by icelechi on 2006-07-08
> **Apple 101 said:**
> What files does it come with? configure? install-sh? autogen.sh?  What programme are you trying to install?  Generally, use ./configure (make and then sudo <password> make install), ./autogen.sh.

It could be in the repositories, so enable Universe and Multiverse (optional) in Synaptic and select Reload.  Then, just search for what you want.

Hi,
Thanks for reading my post and coming to my aid. I tried what you suggested, but I got this message when I typed **make**:
[I]
 *** No targets specified and no makefile found.  Stop.[/I]

Any idea what this means?

---

### Post by aysiu on 2006-07-08
As PriceChild tried to point out, in order to compile from source, you need the *build-essential* package.

Any reason in particular you want to compile *gtkpod* from source instead of just installing it from the repositories?

1. [Make sure you have extra repositories enabled](http://www.psychocats.net/ubuntu/sources)

2. ```
sudo aptitude update
sudo aptitude install gtkpod
```

---

### Post by Apple 101 on 2006-07-08
> **SD-Plissken said:**
> [**[COLOR="Red"]Build-essential installed by default[/COLOR]**]("http://www.ubuntuforums.org/showthread.php?t=192840&page=7") theres seems to be some talk of it being security risk.if this is true or not is unknown.
It wasn't for installed by default for me, however that may be due to it being an alternate installation.

Edit: Unfortunately, the package is still needed, even though it could be a security risk.  However, that is why any issues can be fixed quickly by the community.

---

### Post by John.Michael.Kane on 2006-07-08
Apple 101 i just posted that link cause theres been some talk as to security of said program. as i said if this is true or not is unknown.

---

### Post by aysiu on 2006-07-08
> **Apple 101 said:**
> It wasn't for installed by default for me, however that may be due to it being an alternate installation.
You're quoting SD-Plissken out of context. *build-essential* is **not** installed by default. The _link_ you're "quoting," though, discusses whether or not it should be installed by default.

---

### Post by Apple 101 on 2006-07-08
Okay, okay... That's true.  The thread that was linked by SD-Plissken was discussing that issue.  I'll fix the quote...

---

### Post by Jax Kovak on 2006-07-09
I just installed ASpell and that's working fine, and when I looked in synaptic the CPU monitor was there as well, so thanks for the advice about that.

A couple of things:

Question:
When you install software manually, perhaps with 'make' but maybe without it, are those applications added to synaptic? I ask because I'm pretty sure the CPU monitor program wasn't there before and it clearly is now.

Question:
I took some advice on this forum about installing the Debian Menu system, and it has installed but remains un-usable.

It has appeared in the Alacarte menu editor in the 'System Tools' menu, but will not allow me to select it to make it visible and will not allow me to move it (via drag and drop)

Is there any specific way to get this working?

Thanks

Jax

---

### Post by aysiu on 2006-07-09
For your first question, look into this:
[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

For your second question, try this: ```
sudo chown -R jax:jax /home/jax
``` Assumes, of course, your username is *jax*.

---

### Post by Fossey on 2006-07-10
I'm a complete noob too, i'm not afraid of the command line, i just don't know what to type. I tried typing 

sudo aptitude install gst 

(this was for gstreamer)

It had done
-reading package lists
-building dependency tree
-reading extended state information
-initialising package states

afterwoods i got an error saying 

dpkg was interrupted, you must manually run dpkg --configure -a

so i ran that, and i got another error message saying

dpkg: requested operation requires superuser privilege

---

### Post by user1397 on 2006-07-10
> **Fossey said:**
> I'm a complete noob too, i'm not afraid of the command line, i just don't know what to type. I tried typing 

sudo aptitude install gst 

(this was for gstreamer)

It had done
-reading package lists
-building dependency tree
-reading extended state information
-initialising package states

afterwoods i got an error saying 

dpkg was interrupted, you must manually run dpkg --configure -a

so i ran that, and i got another error message saying

dpkg: requested operation requires superuser privilegethen try **sudo dpkg --configure -a**

---

### Post by Jax Kovak on 2006-07-10
> **aysiu said:**
> For your first question, look into this:
[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

For your second question, try this: ```
sudo chown -R jax:jax /home/jax
``` Assumes, of course, your username is *jax*.

Thanks for the link, Ill look into that. Unfortunately though, the command you suggested didn't work (Or if it did it didn't do anything that I can see!)

The Debian menu is still of no use at all, remaining stuck inside the system menu and refusing to be selected or moved in any way.

---

### Post by digby on 2006-07-10
> **Jax Kovak said:**
> Thanks for the link, Ill look into that. Unfortunately though, the command you suggested didn't work (Or if it did it didn't do anything that I can see!)

The Debian menu is still of no use at all, remaining stuck inside the system menu and refusing to be selected or moved in any way.If there are no items in a menu, alacarte will not allow it to be visible.  If you select it in the left column, you can add entries to it manually, and it will then be able to be made visible.

---

### Post by Jax Kovak on 2006-07-10
Ahhh! Thanks. Yes, the menu is now available and movable, however I'm a little confused with this.

When I installed it I did so because I read an article (on this forum somewhere) that it was a better menu for picking up and detecting installed programs. Right now its just a menu entry with single item in that I duplicated from somewhere else.

Am I missing something here?
Does this 'pick up' your installed programs?

---

### Post by Fossey on 2006-07-10
Thanx for the help, but i still have a problem

after typing sudo dpkg --configure -a

all types of texts came up

setting up python-gnome2 extras
setting up totem
setting up update manager
etc

so i tried running

sudo aptitude install gst

the message said:
couldn't find the package gst and more then 40
packages contain 'gst' in their name
no packages will be installed, upgraded or removed
0 packages will be upgraded, 0 newly installed, 0 to remove and 0 not upgraded
need to get 0b out of archives after packing 0b will be used
writing extended state information...done
etc

and then i go back to where i began... can i please get some help

P.S thanx for the help, these forums rock!

---

### Post by autocrosser on 2006-07-10
Hi Jax--as for the Debian menu--take a look at Synaptic & install "menu"--It "generates programs menu for all menu-aware applications" & will make your Deb Menu work.

You might also take a look at Easy Ubuntu--It will install most of the needed stuff for you....

---

### Post by Jax Kovak on 2006-07-10
Thanks. Menu is already installed, but if I try to use it with "Install-menu" if fails because of a missing script:

```
install-menu: no menu-method script specified!
```

---

### Post by autocrosser on 2006-07-10
OK--Open a terminal (accessories/terminal) &

sudo apt-get install menu

enter your password & then give me the output---

---

### Post by Jax Kovak on 2006-07-10
Thanks autocrosser, here you go, although I'm not sure it will be very much help!

```
Reading package lists... Done
Building dependency tree... Done
menu is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by BluesBoy on 2006-07-10
Hi. Scuse me sticking my nose in. I'm also  a noob with music to do. I tried installing lmms which apparently went ok but nothing has appeared in the applications menu. How do I access lmms? I have the same problem with Rosegarden and Hydrogen. Other apps ( Audacity, Jackrack, Serpentne...) downloaded and installed themselves just fine.

I had a look in Synaptic for Rosegarden and it was there, tagged for re-installation, so it must be in there somewhere.

---

### Post by autocrosser on 2006-07-10
Hi Jax--
Interesting--has this persisted after a reboot?
 
Hi Bluesboy--
Looks like you need menu--go the sudo apt-get route
 
The other thing you can do is set-up a custom app launcher-this can be done via alacarte or right-click on a gnome-panel--you will get a list of items that can be "installed" in the panel & there is a option to create a custom app launcher from there--I'm at work right now, so I can't go into detail--I'll touch base with you guys this evening (6/7 pacific time)

---

### Post by Jax Kovak on 2006-07-11
autocrosser:

Yes, Iv rebooted several times now and the menu remains the same and contains on the single item I put there in order to make it visible!

---

### Post by autocrosser on 2006-07-11
Hi Jax--
Try Easy Ubuntu or Automatix--I seem to recall that there is another app that goes with Menu--I just can't remember which one it is--I upgraded Breezy to Dapper Beta in Oct of last year & I had install the Deb Menu in Breezy (was last Summer :neutral:)

I know in Easy or Auto there is a option to enable the Deb menu--just let one of them do it...

After the Deb menu is in you can use Alacarte to move things around the way you want.

The other thing about these apps--you get many desired apps without hunting thru Synaptic;)

---

### Post by Jax Kovak on 2006-07-12
Thanks for that. Iv been looking at one of these scripts since I discovered mention of them here so Ill dive in and give one a go.

---

### Post by jackson0905 on 2006-07-12
> **icelechi said:**
> Hi,
I am trying to install gtkpod and when I tried ./configure, this was the message that was printed:

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

Any idea what this all means?

maybe ,you haven't install the gcc.
try :sudo apt-get install build-essential

---

### Post by Jax Kovak on 2006-07-12
Thanks autocrosser, its working just fine now! I used EasyUbuntu and everything is now sweet! :D

---

### Post by #1slug on 2006-07-12
When I go to system snaptic package manager isn't there. ](*,) Also when im in add/remove programs it asks for a  password, but my password doesn't work](*,)

---

### Post by MarcG on 2006-07-12
I just moved over from Gentoo to Ubuntu. To make it easy on me I used a "dummy" user when installing and then useradd'ed my old ID, "marc", from the Gentoo days. This was the easiest way to get my old data to just show up with all the right permissions.

But "marc" doesn't have access to the Add/Remove package or the Synaptic drop-down entries. There just aren't any menu picks there. My workaround is to log in as the dummy user to get more packages, or to use apt-get, but how do I allow "marc" to use those fancy package managers?

---

### Post by autocrosser on 2006-07-12
Hi Marc--

take a look at /system/administration/users and groups--check your user for user privileges--make sure that "Executing system administration tasks" is checked--you might check anything that isn't--

I was "playing" with Gentoo early 2004--then I found Ubuntu--Welcome!!!!

---

### Post by BluesBoy on 2006-07-13
Hi Autocrosser,
Thanks for the tip. I'll try it later (just got home from a couple of days away).

---

### Post by MarcG on 2006-07-13
Yeah, thanks, Dean. That was the ticket.

--Marc

---

### Post by autocrosser on 2006-07-13
Hi Marc--

Quite a bit easier that setting flags & emerging everything??

You have three choices--you can sudo apt-get "whatever you want" (if you know what you need--nice easy terminal work)--get aptitude that works in ncurses or use Synaptic (or Gnome-Apt) for the "full GUI" experience...I really like the fact that it's Debian based...Ubuntu came along & shook up the Deb world a bit:-D & made it better for all of us.

---

### Post by aysiu on 2006-07-13
I would advise *aptitude* over *apt-get* in almost all situations.
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

