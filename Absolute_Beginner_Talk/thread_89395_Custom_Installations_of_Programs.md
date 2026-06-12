---
title: "Custom Installations of Programs?"
date: 2005-11-12
forum: Absolute Beginner Talk
---

### Post by dayspring on 2005-11-12
In Windows, minimal/custom installations of programs give me control over my resources, not installing the components I don't use, saving valuable space on my hard drive and keeping my system clean. I like checking the changes made to the hard drive and to the registry after a program is installed.

Two weeks ago I made my first GNU/Linux installation, an Ubuntu 'server' one, so I could decide what to install.
I know Ubuntu is not Windows and there's no reason they should behave the same way, however, I'd like to know how can I make custom/minimal installation of programs like OpenOffice.org, Firefox, Nvu or a window manager. Till now, no options were given during the installation, making me install the whole package even if I knew I was installing things I wouldn't use. And even if I needed them, I like having the option to install the components I want (and learn from that).

One thing I don't understand is the reciprocity of some dependencies. For example, if I install the Spanish language-pack it installs both the Argentine and Spaniard translations of Firefox, but what if I use Opera and I don't want these translations?... Moreover, what if I only want the Spaniard one?... If I try to remove these components, the system also wants to remove the package in their higher level. And this is the kind of reciprocity I don't get.

Thanks for reading.

---

### Post by teaker1s on 2005-11-12
use synaptic manager and advanced mode you can remove some bulk

---

### Post by dayspring on 2005-11-13
Does that mean there are no graphical installers in Ubuntu?... I'm fine with the terminal, what I want are the options during the installation.

---

### Post by Donnut on 2005-11-13
To use graphic installers, you either have to log in as root, (bad idea) and some programs have graphic installers after entering the sudo command to install them.

have fun!

---

### Post by pollentj on 2005-11-13
The advanced view in Synaptic IS graphical. After choosing Add Applications, you get the silly picture-based menu. In the 'file' menu, click Advanced, and you'll get a list of all packages in the repositories you've chosen, with those installed checked. Uncheck one, click Apply, and it's gone.

That's all I know, being a newbie also. 

I've seen all kinds of talk about terminal commands like ./configure, make and make install to manually configure and install apps. I would love some info on how (if at all) I can use these to reconfigure and recompile packages that I get originally through Synaptic.

Anyone?

---

### Post by Dr. Nick on 2005-11-13
Most programs installed using apt-get (synaptic) dont have custom installs. If you install firefox using the linux installer you can do a custom install though. I really dont see a need for custom installs in linux though, most programs are fairly small and dont load you up with garbage. You can use synaptic to remove stuff you dont need , just watch the dependencies removed aswell.

Do you have a specific example of "bloat" you dont want?

---

### Post by pollentj on 2005-11-13
I'm not as worried about bloating and dependencies as dayspring seems to be.
Suppose, though, that I'm using my Ubuntu box as a local testing server for php development and my quirky coding practices require register_globals to be On. It's my understanding that changing such an option involves recompiling, Am i wrong?

(this is hypothetical, so no need to warn me not to use register_globals)

Thanks for your help.

---

### Post by LinuxWiz83 on 2005-11-24
This is not like windows where they extra software besides the one you wanted from the piece of software you wanted. So basicly what were saying this is really no need for custom installs 99% of the time and if there is we suggest you learn how to use apt-get or if there not using apt read there install file for help.

---

### Post by LinuxWiz83 on 2005-11-24
[QUOTE=pollentj]I'm not as worried about bloating and dependencies as dayspring seems to be.
Suppose, though, that I'm using my Ubuntu box as a local testing server for php development and my quirky coding practices require register_globals to be On. It's my understanding that changing such an option involves recompiling, Am i wrong?

(this is hypothetical, so no need to warn me not to use register_globals)

Thanks for your help.[/QUOTE]

Yes your right but apt-get (Synaptics) or any other graphic install on linux won't do recompiling, only basic installs for the most part.

---

### Post by pollentj on 2005-11-24
OK, so I can't use apt-get to recompile my apps with different options.
Does this mean I can't do it?

I assume the answer is that I can do it, but I need to learn how to use make.
Any good resources?

I am specifically interested in whether the package I download through synaptic or apt-get includes everything I'd need to recompile. Or do I need to go out on my own and download a non-Ubuntu-specific version of the source code?
If I were to do this, would the fact that I'm running Ubuntu cause me trouble?

---

### Post by Dr. Nick on 2005-11-26
Some programs have compile time options that let you exclude some aspects of them. It is up to the program developer to make this possible though.

I believe all the application in synaptic are built woth all dfeatures enabled so to increase wide range of compatabality.

To compile without features you need to go to each projects site and get the source code, their should also be a readme with installation instructions which may or may not contain what commads to use to remove features.

It shouldnt be a problem that your using Ubuntu, Just install build-essential package from synaptic before compiling source code. The packages you download in synaptic are pre compiled so they cant be recompilied, you have to get the source code.

Hope that clears it up some, Good luck

---

### Post by gord on 2005-11-26
most of the time, if you are enabling/disabling fetures when you compile youself you'll only be changing the final size by a very small amount and its usually just for compatibility reasons. 

i think the real answer is that the way linux works allows you to make your own custom installations of everything, a windows app that uses sdl might have to pack sdl.dll into its installer to put in its directory or \windows. with linux you can choose to not install sdl yourself, allthough since the program _needs_ it, apt would install it for you if you don't allready have it. 
most of the time, the program needs everything it installs. a nice example might be the ammount of themes that you can install using gnome, there are a lot of them but only a few are pre installed and you can remove/add which ever you want.

---

### Post by em4r1z on 2008-03-23
Sorry for bringing back a three years old thread but I have the same doubts the original poster had: are there custom installations of programs in Linux?
In Windows, all installers give you advanced options during the installation, letting you choose what and where to install.

If I install Firefox in Windows, I can choose not to install the bug report and web developer add-ons, if I install it in Linux I have to uninstall them after the installation. I can live with this. Now, things get more complicated when you install a large package like OpenOffice.org. A custom installation really matters for the differences are not a couple of Kbytes and a 'remove this' step: if I install OO.o in Windows I can control dozens of things during the installationg, letting me choose the components, documentation, languages and add-ons to install. What if I only use Impress and Writer but not Base, Calc and Draw?, what if I'll only use one language pack and not the tens available?

The 'problem' is the same in both cases: why would I install something I'm not going to use (whether it's a small add-on or a huge set of office applications)?... It's just not efficient.
Please, don't come to me with the 'HD are so cheap these days that...' answers. Technology is based in the opposite logic.

---

