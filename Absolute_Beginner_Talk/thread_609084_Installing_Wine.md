---
title: "Installing Wine"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by tstormdamage on 2007-11-10
I have attempted to install Wine by following the directions at [http://winehq.org/site/download-deb]("http://winehq.org/site/download-deb") for Gutsy, but I receive the following messages when I type in > sudo apt-get install wine
 > Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: binfmt-support (>= 1.1.2) but it is not installable
        Depends: libaudio2 but it is not installable
E: Broken packages
 What does this mean and how can I fix it. I'm a complete newbie to Linux. All help will be greatly appreciated

---

### Post by Maestro23 on 2007-11-10
Make sure all your Repositories are enabled: System>>Admin>>Software Sources

Search for** libaudio2** in Synaptic and install it. (System>>Admin>>Synaptic).

---

### Post by t3h_h4ck3r on 2007-11-26
What happens if you dont have internet on your ubuntu (gutsy 7.10) machine, but you have wine on a flash disk, what dir do you install to?

---

### Post by CatKiller on 2007-11-26
> **t3h_h4ck3r said:**
> What happens if you dont have internet on your ubuntu (gutsy 7.10) machine, but you have wine on a flash disk, what dir do you install to?

See, for example, ["How to install ANYTHING in Ubuntu"]("http://monkeyblog.org/ubuntu/installing/").

The way installing works if you have an Internet connection is that you select which package you want to install, and Ubuntu looks at the list of dependencies to see if there's anything that you need that you don't have. Then it adds those dependencies to the list of files that it needs to download and install. In this case, the dependency is that you can't install the latest version of Wine without a recent version of libaudio2. There may be other dependencies too.

Since you don't have the Internet connection needed for it all to happen automagically, you'll need to do the heavy lifting yourself. There is a list of Ubuntu packages at [http://packages.ubuntu.com](http://packages.ubuntu.com), and you can check and retrieve the dependency files from there. You may need to make a few trips of it turns out that you have dependencies of dependencies or what-have-you. This automation is a big labour-saving device.

Once you've got all of your .deb files on your together, you can **cd** to wherever you've got them all, either on your flash drive or on your computer, and then use ```
sudo dpkg -i package1.deb package2.deb package3.deb
``` where package1, package2 and so on are the names of the .deb files that you want to install. You can use Tab-completion to fill in the names of the files to avoid any typos - type the first few letters of the filename and then press Tab, and it will fill in the rest for you.

The rest should happen automatically.

Good luck!

---

