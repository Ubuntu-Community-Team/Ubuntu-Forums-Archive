---
title: "ndiswrapper modules"
date: 2005-11-10
forum: Absolute Beginner Talk
---

### Post by samdude9 on 2005-11-10
hi
new to ubuntu and just reconpiled the kernel.
I now cant use the prog (ndiswrapper) i need the module so...
please can you tell me how to get the modules + install them without apt-get in have a pc here with the net and a usb key.
thx
bye

---

### Post by etc on 2005-11-10
Do you have ndiswrapper installed already?
If you do try modprobing ndiswrapper
sudo modprobe ndiswrapper

---

### Post by az on 2005-11-10
Next time you recompile the kernel, use the ubuntu source with ubuntu patches.  You will have the ndiswrapper source included.

Gte the tarball from the ndiswrapper home page and (I think) you run the debian scripts to build two debian packages (utils and modules)

Obviously, do this on the same machine you build the kernel on and use the source tree.

tar xvzf ndiswrapper*
cd ndiswrapper
sudo debian/rules/binary



(Read the readme since this is all from memory)

---

### Post by bluefrog on 2005-11-10
not sure I understand why you recompiled the kernel.

anyway ndiswrapper is on the cd.
so fresh install
install ndiswrapper (from the cdrom you have) with synaptic or apt-get and then configure.

mkdir /home/drivers
cp <path-to-drivers>.inf /home/drivers
cp <path-to-drivers>.sys /home/drivers
ndiswrapper -i /home/drivers

to check:
ndiswrapper -l

to load:
modprobe ndiswrapper

to load on boot:
ndiswrapper -m

---

