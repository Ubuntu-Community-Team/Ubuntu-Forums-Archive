---
title: "compiling a tar file"
date: 2005-10-23
forum: Absolute Beginner Talk
---

### Post by PriceChild on 2005-10-23
Hey, i'm trying out eciadsl and have download the source file (*.tar.gz) however i'm a beginner and need to find out how to use this file... must i compile it first? how would i do that? Commands for that in the console?

Once compiled should i be able to right click the new file and select an option to install it or something?

Thanks in advance for any time you spend helping, Pricey

---

### Post by PriceChild on 2005-10-23
Ah... just realised i should download the debian driver instead... will have a quick look see what i can do with that :)

pricey

Please still give advice on how to solve this as i probs won't figure it out lol :)

---

### Post by mostwanted on 2005-10-23
For some other time, here is the answer to your question:

.tar is a non-compression archive format. tar.gz is tar with gzip compression applied to it. Normally these packages contain source code, so yes you'll have to compile it. Fortunately that's dead simple.

First you unzip the contents, go to the folder of the file and run
```
$ tar -zxvf mypackage.tar.gz
```

Then you go inside that folder which was created. Use ls and look after a folder name that looks like your tar file's name (without the extension).

Then you do the so called ./configure, make, make install combo
```

$ ./configure
$ make
$ sudo make install
```

Sometimes, there's no configure script, so don't be sad if it gives you an error output :)

Anyway, then your program should be installed!

---

### Post by PriceChild on 2005-10-23
Thanks very much... attempting.... :P

---

### Post by PriceChild on 2005-10-23
Ok... still noobish status... how do i navigate inside the terminal?

And is there an easier way using the debian file?

Thanks, Pricey

(put everything in my home folder for simplicity)

---

### Post by David Marrs on 2005-10-23
The first thing to do is to search to ubuntu repositories for a prebuilt package using synaptic (or the terminal program apt-get if you prefer). If it's not there then you should start hunting around for deb packages and try installing them with dpkg -i package.deb. If you can't even find a deb package (or it doesn't work because this is ubuntu) then you should install from source.

These aren't hard and fast rules but they do ensure the easiest ride.

The terminal's a bit cryptic but it's quite simple to use and there are plenty of manuals online to help explain it. Google for "unix shell" or "unix commands" to find a good tutorial. I found [this one](http://www.phys.ualberta.ca/~gingrich/research/shells/shells.html), which looks quite good.

---

### Post by aysiu on 2005-10-23
[quote=PriceChild]And is there an easier way using the debian file?[/quote]
Yes, forget the .tar.gz.

Follow these instructions to enable extra repositories:
[http://www.psychocats.net/sources.html](http://www.psychocats.net/sources.html)

Then, type these two commands in the terminal ```
sudo apt-get update
sudo apt-get install eciadsl
```

---

### Post by shanghaipi on 2005-10-23
I just tried to install Yamipod from a tar.gz file...and this is what I got...(I extracted it to my home folder with ubuntu's archive manager...)

root@ubuntu:~# cd /home/localbob/yam-linux
root@ubuntu:/home/localbob/yam-linux# ./configure
bash: ./configure: No such file or directory
root@ubuntu:/home/localbob/yam-linux#


I tried it without using Root, but I had the same results...I must be doing something wrong that's totally obvious.

---

