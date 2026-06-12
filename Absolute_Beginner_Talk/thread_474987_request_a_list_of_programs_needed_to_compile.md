---
title: "request: a list of programs needed to compile"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by teripittman on 2007-06-15
I'm trying to recompile Jpilot after having to completely reinstall Ubuntu. This is always frustrating because the script will run and then ask for something. Add that and it wants something new. I installed gcc but that does not seem to be enough and now I'm trying to figure out what other programs I need to install. I can usually do that but it would be nice if someone could pull together a list of commonly needed programs that allow you to use ./configure-make-make install.

Thanks!

---

### Post by Golyadkin on 2007-06-15
Try 
> 
sudo apt-get install build-essential


That should get you a long way.

---

### Post by pnix on 2007-06-15
apt-get source jpilot
sudo apt-get build-dep jpilot <--- install dependencies

---

### Post by samuraiCat on 2007-06-15
> **pnix said:**
> apt-get source jpilot
sudo apt-get build-dep jpilot <--- install dependencies

Could you explain to a newbie (me) what exactly that will do? Thanks!

---

### Post by Golyadkin on 2007-06-15
If you are a newbie, welcome to the 'man' command. If you type 'man' and then the name of a program, it will show you a manual for the command. Isn't that handy? 

For instance, I just typed: "man apt-get source" in the console and got a lot of info, among which:
> 
**source**
          source causes apt-get to fetch source packages. APT will examine the
          available packages to decide which source package to fetch. It will
          then find and download into the current directory the newest
          available version of that source package. Source packages are
          tracked separately from binary packages via deb-src type lines in
          the sources.list(5) file. This probably will mean that you will not
          get the same source as the package you have installed or as you
          could install. If the --compile options is specified then the
          package will be compiled to a binary .deb using dpkg-buildpackage,
          if --download-only is specified then the source package will not be
          unpacked.

          A specific source version can be retrieved by postfixing the source
          name with an equals and then the version to fetch, similar to the
          mechanism used for the package files. This enables exact matching of
          the source package name and version, implicitly enabling the
          APT::Get::Only-Source option.

          Note that source packages are not tracked like binary packages, they
          exist only in the current directory and are similar to downloading
          source tar balls.


and also

> 
** build-dep**
          build-dep causes apt-get to install/remove packages in an attempt to
          satisfy the build dependencies for a source package.


Which answers both your questions :)

---

### Post by teripittman on 2007-06-15
Oh, I know about man pages. I'm not that noob! And it was easy enough to fix the first error when it needed gcc. The thing is that you go into Synaptic package manager to pull up these programs and there's usually a list of unrelated programs. In one case, I had to have a dev package installed for compiling to work. Sometimes the error messages on the scripts don't really tell you what is needed. So it seems like it would be good to have a list of basics that will compile most programs.

And aren't we supposed to use "aptitude" instead of apt-get now??

---

### Post by ramjet_1953 on 2007-06-15
Is there a particular reason why you want to compile JPilot?

It is already available in the repositories and can be installed with Synaptic.

Just do a search in Synaptic for[COLOR="Blue"] jpilot[/COLOR] and it will be dispayed, along with companion packages.

Regards,
Roger :cool:

---

