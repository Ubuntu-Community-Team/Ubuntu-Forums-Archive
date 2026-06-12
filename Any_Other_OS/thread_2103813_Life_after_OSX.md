---
title: "Life after OSX"
date: 2013-01-11
forum: Any Other OS
---

### Post by outofsync on 2013-01-11
Hi,

First of all, I'd wish that this discussion stays away from flamewars against any OS. I say this because I've almost discarded Ubuntu as my next OS, but I don't pretend any flamewar, just a positive talk about other options out there.

In the past, decades ago, I've been an SGI IRIX user. Later I moved to Mac OSX and Ubuntu, and used both OSs on a daily basis. But for the last years, I've been using OSX almost 100% of the time.

However, recent Apple policies, by putting the UI into crisis, turning OSX friendly for iOS users but unfriendly for long-time computer users, makes me consider options in case OSX becomes finally unusable (I hope not, but it can happen, and it's likely to happen).

Last october I installed Ubuntu 12.12, for looking how it has evolved after these years, and I cannot live with it, for the same reasons I don't like new Apple changes. It's not a matter of Gnome3 vs Unity, because I don't like Gnome3 either.

So I've beginning to look at Debian, whose change of default desktop to Xfce made me think "these dudes have something different to say", but later they've reverted the default desktop to Gnome3, a decision that disappoints me.

Yes, I know I can change the desktop on both Ubuntu and Debian, but I want an OS whose developers have my same opinion about what a powerful desktop is, and neither Ubuntu nor Debian seem to share my point of view about desktops.

At the same time, there're a couple of features I find very powerful on OSX, but, AFAIK they aren't available on Linux (or at least they're not widespread):

1 - **_Application bundles_**: It's great to ship your apps in a way that no installer nor uninstaller is needed. All the app paths are relative to the bundle directory, all files the app needs are inside the bundle directory, and the user sees the directory as an application rather than a directory. This is GREAT, and I'd love to continue developing software in this way FOREVER.

2 - **_Disk images_**: The way DMGs and ISOs are managed on OSX is great. The desktop handles them in a transparent way, just like if they were normal folders. They can be even compressed, and they can be made read-only or writable. Just great. I'd love to continue having this feature FOREVER :D

Of course there're other things I love from OSX (like stacks on the dock, fat binaries for having 32bit+64bit executables on the same binary, as well as the UI looks -but Lion made an step backwards on the UI look), anyway, these other things aren't as important to me as application bundles and disk images.

Do you've any OS to recommend me for the future? Or will I be without alternatives if OSX becomes trashed?

Thanks!!!

---

### Post by mamamia88 on 2013-01-11
> **outofsync said:**
> Hi,

First of all, I'd wish that this discussion stays away from flamewars against any OS. I say this because I've almost discarded Ubuntu as my next OS, but I don't pretend any flamewar, just a positive talk about other options out there.

In the past, decades ago, I've been an SGI IRIX user. Later I moved to Mac OSX and Ubuntu, and used both OSs on a daily basis. But for the last years, I've been using OSX almost 100% of the time.

However, recent Apple policies, by putting the UI into crisis, turning OSX friendly for iOS users but unfriendly for long-time computer users, makes me consider options in case OSX becomes finally unusable (I hope not, but it can happen, and it's likely to happen).

Last october I installed Ubuntu 12.12, for looking how it has evolved after these years, and I cannot live with it, for the same reasons I don't like new Apple changes. It's not a matter of Gnome3 vs Unity, because I don't like Gnome3 either.

So I've beginning to look at Debian, whose change of default desktop to Xfce made me think "these dudes have something different to say", but later they've reverted the default desktop to Gnome3, a decision that disappoints me.

Yes, I know I can change the desktop on both Ubuntu and Debian, but I want an OS whose developers have my same opinion about what a powerful desktop is, and neither Ubuntu nor Debian seem to share my point of view about desktops.

At the same time, there're a couple of features I find very powerful on OSX, but, AFAIK they aren't available on Linux (or at least they're not widespread):

**1 - [B]_Application bundles_**: It's great to ship your apps in a way that no installer nor uninstaller is needed. All the app paths are relative to the bundle directory, all files the app needs are inside the bundle directory, and the user sees the directory as an application rather than a directory. This is GREAT, and I'd love to continue developing software in this way FOREVER.[/B]

2 - **_Disk images_**: The way DMGs and ISOs are managed on OSX is great. The desktop handles them in a transparent way, just like if they were normal folders. They can be even compressed, and they can be made read-only or writable. Just great. I'd love to continue having this feature FOREVER :D

Of course there're other things I love from OSX (like stacks on the dock, fat binaries for having 32bit+64bit executables on the same binary, as well as the UI looks -but Lion made an step backwards on the UI look), anyway, these other things aren't as important to me as application bundles and disk images.

Do you've any OS to recommend me for the future? Or will I be without alternatives if OSX becomes trashed?

Thanks!!!
Application bundles?   Well they do have tarballs for some applications like firefox where you can just extract it and double click a binary file in the folder.  But i personally find apt-get install firefox isn't any more difficult.  As far as isos not sure don't use it often enough.    Go with xubuntu and install a third party dock with synapse quick launcher and I feel like you will feel right at home.  The xfce4 places plugin is somewhat like stacks.  You can even install compiz to have some of the same visual effects but it's not nescessary .

---

### Post by Thee on 2013-01-11
If you want something OSX-like, take a look at ElementaryOS:
[http://elementaryos.org/journal/when-its-ready](http://elementaryos.org/journal/when-its-ready)

---

### Post by iMac71 on 2013-01-11
Hi outofsync,
let me tell you something about my experience with OSX and Ubuntu.
I used OSX for many years, from Jaguar to Snow Leopard, and I was always happy with these versions: they have always worked fine, and, as you say, they were extremely easy to use.
Starting from OSX Lion, the things have changed in worse: more hardware requirements, an UI redesigned specifically for being used on portable devices like iPods, iPhones and iPads, and less attention to Mac users.
For this reason, and since I didn't wish to spend money for a new computer considering that my iMac works well, I decided to abandon OSX and to install Ubuntu.
As you say, there are differences between OSX and Ubuntu, but IMHO Ubuntu is quite similar to OSX, hence there aren't big problems for using that OS.
Just some examples:
1) you want to uninstall an application: simply type in a Terminal these commands:
```
sudo apt-get purge -y application_name
sudo apt-get autoremove -y
```as an OSX user, you shouldn't have problems using the Terminal;
2) ISO images: you may use Brasero or Gparted or Archive Manager, depending of what you want to do.
Give a chance to Ubuntu to be yours new unique OS, and you'll find that it's not so hard to use.

---

### Post by drawkcab on 2013-01-11
Linux is modular.  Instead of thinking of yourself as tethered to a particular desktop environment, install and session into whichever suits you.

I would think xubuntu with cairo dock would suit you well.  You may want to try kubuntu which features kde.

Off the top of my head, pear, luninux and a few others have tweaked Gnome shell to work like mac OS.  Pinguy OS has some radical ideas of what a desktop should be.  And yeah, Elementary OS is finishing off an innovative desktop that should be the first game changer since unity and gnome shell.

---

### Post by craig10x on 2013-01-11
He could also simply install cairo dock (which will remind him very much of the dock in osx) on ubuntu 12.10 and use the "cairo dock session" from the ubuntu log in screen (the one with no unity dock but with the top "global menu" unity top panel)....

But before installing cairo dock, try using unity for about a week...you may find you get to like it a lot...that is what happened to me ;)

I simply added all my favorite apps and frequently used ones, to the unity dock bar and on the rare times i need some other app i just type it into the "dash" (unity search) and bring it up!

---

### Post by iMac71 on 2013-01-11
Just another couple of things about Ubuntu:
1) on OSX we have Spotlight for finding files and applications; in Unity - the standard desktop environment starting from Ubuntu 11.04 - we have Dash, that can be invoked simply by pressing the SUPER key (i.e. the Windows key on Windows keyboards);
2) imagine that you're using an application that has a lot of menu commands and that you don't remember which menu contains the command you wish to use: well, Unity offers a very simple and easy to use solution: the HUD; you only have to press the ALT key from within the application and to type the command name you're looking for and finally to press ENTER key: the command is immediately executed. AFAIK there isn't an equivalent way on OSX.

---

### Post by iMac71 on 2013-01-11
> **craig10x said:**
> He could also simply install cairo dock (which will remind him very much of the dock in osx) on ubuntu 12.10 and use the "cairo dock session" from the ubuntu log in screen (the one with no unity dock but with the top "global menu" unity top panel)....

But before installing cairo dock, try using unity for about a week...you may find you get to like it a lot...that is what happened to me ;)

I simply added all my favorite apps and frequently used ones, to the unity dock bar and on the rare times i need some other app i just type it into the "dash" (unity search) and bring it up!IMHO docky is the most similar dock to the OSX's one, even regarding to the appearance; but you're right, before of installing any docks it's preferable to try Unity for some time.
BTW: personally I like Unity very much.

---

### Post by craig10x on 2013-01-11
yes, imac71, one week using unity and he will love it (he says as he sends out hypnotic rays at the op) :D

seriously, he should give it about a week...he might be surprised how quickly it "grows on you"...

yes, that's true, docky would be the closest...though the reason i mentioned cairo dock is because a separate session is set up for it that he can use without unity dock on it...

---

### Post by MadmanRB on 2013-01-11
Yeah I like cairo dock/docky as a suggestion too, it does make unity more fun to use.
as for what the OP is blathering about honestly I never had an issue with using stuff like synaptic or even ubuntu software center to install packages and really its not that hard to install things under ubuntu.

---

### Post by drawkcab on 2013-01-12
Docky seems to crash a lot in xubuntu.  I'm sure there's some fix for this but it's annoying.  Cairo is obnoxious but you can tone it down via settings.

---

### Post by ugm6hr on 2013-01-12
My thoughts:
1. Application Bundles
This reminds me of the old RISC OS. I haven't used OSX (except on other people's computers), so wasn't aware of this "feature." RISC OS is being released on the Raspberry Pi, but is not open source, and I suspect the Pi won't live up to your PC needs!
I (briefly) dabbled with ROX-desktop, which was supposed to mimic this, and was inspired by RISC OS GUI, but I'm not sure it's being developed any more. Not sure if the feature continues with zero install [http://0install.net/](http://0install.net/) - but I think that was the "base" for the feature in ROX.
2. ISO management
I don't know of any file managers which feature seamless ISO mounting, but nautilus plugins used to achieve this, as does GmountISO, though I just use terminal. Once mounted, you can access files, although I have never tried changing permissions in an ISO.
3. GUI looks
If you like OSX - I would suggest Elementary OS (Pantheon DE), although it is strictly still in Beta.

---

### Post by montag dp on 2013-01-12
As far as desktops go, I've been using KDE for awhile now and I have to think it's the best in terms of ability to be customized.  You can adjust pretty much anything so that it works exactly the way you want, which should definitely fulfill your usability requirement.  The downside is that, because there is so much possible customization, the learning curve is probably a bit higher than most other desktop environments.  But, I've never had a problem finding any information I needed by searching.

---

### Post by BBQdave on 2013-01-13
> **iMac71 said:**
> I used OSX for many years, from Jaguar...

since I didn't wish to spend money for a new computer considering that my iMac works well, I decided to abandon OSX and to install Ubuntu.

Similar paths :)

My eMac is now a file server on my home network. Completely stepped away from Mac's and now use Linux for work and play.

Over the span of a few short years, I burned through 2 iBooks and 1 MacBook. The solution offered me by Apple on the fail of my MacBook - buy new Mac hardware...

I have found Mac to have neither superior software or hardware - yet they charge a premium price. 

Happy to use Ubuntu Unity 12.04 on a Toshiba notebook - very productive and hardware going strong. My back up notebook is a decade old Dell Inspiron with Debian 6 - still functions well.

If you are going to hang with Apple - best to have deep pockets :p

---

### Post by Max Blyss on 2013-01-13
One must step away from their conception of what a desktop should be and just add a whole bunch of weird stuff that looks neat.  Yeah, that's the ticket.:P

For real, though...  I've been trying EOS, and that is one easy-to-use, convenient DE they have.  It's like an almost total re-work of Gnome 3, but it is so fast and simple that it's amazing.  Still in beta, but I haven't noticed any problems in it.  If you're looking for a straightforward, feature - rich kinda thing, keep your eye on those folks.

---

### Post by outofsync on 2013-01-16
> **iMac71 said:**
> 
1) you want to uninstall an application: simply type in a Terminal these commands:
```
sudo apt-get purge -y application_name
sudo apt-get autoremove -y
```as an OSX user, you shouldn't have problems using the Terminal;

My wish of having "app bundles" on any OS I choose from today on is both from a user perspective, and from a developer perspective:

a) From a user perspective: One of my favorite things about OSX is that applications don't need installation, so this means no files are put outside the app directory. Installation is just dragging such directory to some place. Uninstallation is just removing the directory. So, no libs are left in the libs directory, no manpages are left on the man directory, no services are left on the boot procedure... and the operating system manages the app directory like if it was an object: the app-bundle. The user doesn't see the contents of the app-bundle unless he explicitly wants to see its contents. Otherwise, he just sees an icon, although OSX knows there's a directory structure "behind the icon".

b) From a developer perspective: I've been a UNIX user and developer for quite a few years, before using OSX. And developing a UNIX application always had the complication of "spreading" files across system directories (/bin, /lib, /etc, and so on), so when I was developing an application and somebody wanted to try it on their machine, it was an annoyance because I had to prepare an installer for him to try it. When I moved to OSX and found how apps are distributed, I joyfully exclaimed "this is how I always wanted to ship apps: neither the traditional UNIX way, nor the buggy Windows installers way... the OSX way just rocks, because of its simplicity).

> **iMac71 said:**
> 2) ISO images: you may use Brasero or Gparted or Archive Manager, depending of what you want to do.
Give a chance to Ubuntu to be yours new unique OS, and you'll find that it's not so hard to use.

Never tried them, but I'll give it a try.

Thanks for all your comments!!

---

