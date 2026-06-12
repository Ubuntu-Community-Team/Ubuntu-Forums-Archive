---
title: "Dependancy And Conflict Resolutions?"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by Accurax on 2007-04-24
Im following this installation guide for hplip [http://hplip.sourceforge.net/install/install/index.html]("http://hplip.sourceforge.net/install/install/index.html")

I'm currently on Step 7 ...... It says it "may take several minutes" .... getting concerned now as its been about 15 minuites which is more than several.

I have (as far as i know) correctly activated the multi verse thingy ...... has anyone been through this installation themselves?

Im getting really upset at not being able to get this to work..... someone help me please ... dont make me beg :(

---

### Post by Skrynesaver on 2007-04-24
Ahh, this isn't quite the way to do things, most packages you find will be Ubuntu and you should use these packages rather than just unzipping some binaries across your system.
if you find a package you need (hplip) you should do an apt-cache search for the package, this means that the packet manager will maintain this package for you, keep it up to date .... eg
```

~$ apt-cache search hplip
hpijs - HP Linux Printing and Imaging - gs IJS driver (hpijs)
hpijs-ppds - HP Linux Printing and Imaging - HPIJS PPD files
hplip - HP Linux Printing and Imaging System (HPLIP)
hplip-data - HP Linux Printing and Imaging - data files
hplip-dbg - HP Linux Printing and Imaging - debugging information
hplip-doc - HP Linux Printing and Imaging - documentation
linuxprinting.org-ppds - linuxprinting.org printer support - PostScript PPD files
hpoj - HP OfficeJet Linux driver (hpoj)

```
So the package we need is probably hplip itself
```
apt-cache show hplip
```
gives us a rundown of the package, That looks about right so we do a 
```
sudo apt-get install hplip
```
This means we're using the correct version and it is installed as Ubuntu requires.

---

### Post by urukrama on 2007-04-24
If you feel uncomfortable using the command line (doing an "apt-cache" search), you can also use Synaptic Package Manager (in the System menu); then just do a search for the package/appication you are looking for, select it (through right click) and press "apply". You can also search for key terms (say mp3, browser, text editor, etc.)

This way of installing applications may feel strange and complicated at first (if you are used to a non-Linux OS), but once you get the hang of it, you'll love it.

---

