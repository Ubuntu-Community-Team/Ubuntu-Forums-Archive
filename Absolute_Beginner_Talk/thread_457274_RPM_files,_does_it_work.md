---
title: "RPM files, does it work ?"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by akkad on 2007-05-28
does ubuntu run rpm files?
if i want to get any application setup from the internet for ubuntu which file extension(ex: rpm, deb, tar ...) i should download for the easiest installation as i am new to ubuntu ????

---

### Post by Happy_Man on 2007-05-28
.deb files are easiest, as Ubuntu is a debian-based distro.

You can convert rpms to debs, but go with debs for now.

And .tar.gzs are a pain in the @$$.

---

### Post by aysiu on 2007-05-28
.rpm files can work, but those should be one of your last resorts. Read more here:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by benanzo on 2007-05-28
Ubuntu handles .DEB files natively.  It does not handle RPMs.  It is, however, trivial to convert an RPM to a DEB with a utility called **alien**

Open and terminal **Applications -> Accessories -> Terminal**
and type:
```
sudo apt-get install alien
```

This will download and install **alien**.

When it is finished, navigate to the place you have download the RPM file eg:
```
cd /home/you/Desktop
```
(if it's on your desktop)
and do:
```
sudo alien name_of_rpm.rpm
```

It will then convert it to a DEB and install it.

Packages that have the .tar.gz (or .bz2) extension are usually source code.  If this is the case, you can just right-click them and select **Extract Here**

In order to compile source code you need to have the proper packages installed first:
```
sudo apt-get install build-essential linux-headers-$(uname -r)
```

Then change into that directory in a terminal -
(eg if the new source directory is on your desktop) :
```
cd /home/you/Desktop/new_source_dir
```

To configure that package do:
```
./configure
```
Then to compile it do:
```
make
```
Then to install it do:
```
make install
```
OR
You can package that source code into a .DEB file that can be easily managed by Synaptic by using a utility called **checkinstall**
```
sudo apt-get install checkinstall
```

Then, instead of doing
```
sudo make install
```
you do:
```
sudo checkinstall
```

This will produce a .DEB file that can be easily uninstalled later.

It is also possible for a piece of software to be distributed as binary-only and be packaged as a **tar.gz** or **tar.bz2**.  In this case you usually only have to extract the directory and double-click the binary file inside.

---

### Post by akkad on 2007-05-28
ok am trying to install vmware, after installing alien i executed 
"sudo alien -i VMware-workstation-5.5.4-44386.i386.rpm" where the output was 
Warning: Skipping conversion of scripts in package VMwareWorkstation: postinst postrm preinst prerm
Warning: Use the --scripts parameter to include the scripts.

then the terminal it seems waiting to enter some commands, any idea??

---

### Post by Happy_Man on 2007-05-28
If it looks like this:
```
akkad@akkad:~$sudo alien -i VMware-workstation-5.5.4-44386.i386.rpm
Password:
akkad@akkad:~$
```

Then it's not doing anything.

If it looks like this:
```
akkad@akkad:~$sudo alien -i VMware-workstation-5.5.4-44386.i386.rpm
Password:


```

Then it's working. Be patient; this takes a bit.

---

### Post by akkad on 2007-05-29
i got ur point, after i entered the password it started directly the conversion process to deb file but it doesnt completed the whole process where the warnings i mentioned previously appeared, the proof that same file with  the same name created but with deb extension, then when i double click the created deb file an error appear tells that the file is corrupted, so i think the alien process didnt finish, where the terminal needs an input, i wonder what is it ???

---

### Post by akkad on 2007-05-29
ooops u were totally right, the process took a long time, vmware installed but i still have problem in vmware installation guide so i will check with vmware, thnx anyway.

---

