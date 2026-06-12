---
title: "Installing Mac applications in Ubuntu"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by cool_penguin on 2007-09-13
Hi Guys,

I am a Linux newbie. Is it possible for one to install .dmg (mac applications) on Ubuntu. Since Mac OSx and Linux are cousins (similar to Unix), is it possible for one to convert a .dmg to something like .deb which can then be installed on Ubuntu. 

I am aware of installing Linux applications on Mac without any emulators, but i was wondering, if a similar thing could be done vice-versa.

Thanks a lot in advance.

Cheers,
Harry

---

### Post by kerry_s on 2007-09-13
no

---

### Post by Tomosaur on 2007-09-13
> **cool_penguin said:**
> Hi Guys,

I am a Linux newbie. Is it possible for one to install .dmg (mac applications) on Ubuntu. Since Mac OSx and Linux are cousins (similar to Unix), is it possible for one to convert a .dmg to something like .deb which can then be installed on Ubuntu. 

I am aware of installing Linux applications on Mac without any emulators, but i was wondering, if a similar thing could be done vice-versa.

Thanks a lot in advance.

Cheers,
Harry

I was also looking for some way to do this a while back. As far as I'm aware it can't yet be done - and in any case I would assume we'd need to use some compatability layer like Wine. While Macs are very similar to Linux, the two are also different in many ways.

That being said - .dmg files are just compressed files, and you CAN access them - although it probably won't be of much use since you still won't be able to run the binaries enclosed within. Go to [this web site]("http://vu1tur.eu.org/tools/"), and download dmg2img source code. Now, you will need the build-essential package in order to compile from source code, so open up a terminal and type:
```

sudo apt-get install build-essential

```Now, you need to compile dmg2img. In the terminal, use 'cd' to get to wherever the source code archive downloaded to, then:
```

tar -zxvf ./dmg2img.tar.gz
cd dmg2img
make all

```

Once that's done, use the following commands to convert, then mount, the .dmg file:

```

./dmg2img -i /path/to/dmg_file_to_convert.dmg -o /path/to/img_file_to_output.img
sudo modrobe hfsplus
sudo mount -t hfsplus -o loop /path/to/img_file.img /mount_point

```Now you need to change to the mounted directory, and you'll be able to see the files contained in the .dmg file:
```

cd /mount_point
ls

```Hope that helps! At least you'll be able to see what's inside the .dmg file, and you MAY be able to find a way to run the software, but I suspect most, if not all, Mac software will simply not run on Linux. The easiest solution is to just use Linux software.

If you can find Mac software which is open source, you me able to compile a version so that it runs on Linux.

---

### Post by framebuffer on 2007-10-13
Too bad,

I came across this great study card software that I wanted to try:

[http://www.digitalmeadow.com/](http://www.digitalmeadow.com/)

They have a lite version available for evaluation. I wanted to try it on linux. I am somewhat surprised to learn that linux can run windows apps (I am running winflash educator 8 using wine) but cant run a Mac application.

---

