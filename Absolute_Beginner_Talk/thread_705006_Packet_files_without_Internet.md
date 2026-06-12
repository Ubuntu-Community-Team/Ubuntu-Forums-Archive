---
title: "Packet files without Internet?"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by infinityandthevoid on 2008-02-22
Unfortunately, the computer I want to install Ubuntu on isn't connected to the internet.
I was reading up on Ubuntu (because I'm itching to try it) and I saw the packet files. I think this is a great idea but it says it installs from the internet :S Can I still use these?

I asked one of my friends and he said I would have to find .deb file and manually "compile" them.
Any help is appreciated.
Thanks.

---

### Post by infinityandthevoid on 2008-02-22
I read up on the subject here:
[https://help.ubuntu.com/7.10/add-applications/C/install-file.html](https://help.ubuntu.com/7.10/add-applications/C/install-file.html)

Can I do the same thing with a package file?

---

### Post by ShodanjoDM on 2008-02-23
You can use Synaptic to generate download script. It contains necessary packages of any programs and their required dependencies.

1. Open Synaptic from your user account (type synaptic in the terminal). This way you can't install or uninstall programs but you still can generate package download script. 

If you run it as root, the generated download script will have root privileges, so running as normal user will save some hassles if you want to read or copy/delete the script.

2. Pick any programs you want (Synaptic will automatically marks required dependencies).

3. At the menu bar,  click File > Generate package download script.

4. Pick your location. Your home folder is the default since you're running it as normal user. For simplicity, choose Desktop.

5. Name the script and save.

6. You can now open and read the script that it's contain links like this:

```
#!/bin/sh
wget -c http://archive.ubuntu.com/ubuntu/pool/universe/g/grml-shlib/grml-shlib_1.02.11ubuntu3_all.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/multiverse/l/lame/lame_3.97-0.0_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/universe/m/mp3info/mp3info_0.8.4-9.2_i386.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/multiverse/a/a2mp3/a2mp3_0.01-0ubuntu2_all.deb
```

In the example above I picked a2mp3 and Synaptic automatically picked its dependencies. You see that there are web links for each packages as well.

Now all you have to do, is copy the script to a portable drive, go to internet connected PC, download the packages one by one and when you get home, just put all of the downloaded packages in one folder and run this inside the folder:

```
sudo dpkg -i *.deb
```

It will install all *.deb packages in that folder.

It's a bit awkward, but it works.

---

### Post by infinityandthevoid on 2008-02-23
Thanks alot for the help.
I'm installing Ubuntu right now so I'll let you know how your method went.

---

