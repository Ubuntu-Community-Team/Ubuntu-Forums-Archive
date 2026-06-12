---
title: "No sound."
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by jerrynor on 2007-05-20
Video works just fine.  No sound from CD or video sources. Volume settings correct.

Card: 82801G intel

Laptop: Toshiba P105

Card listed by aplay -l

ALSA driver hda-intel installed I think.  At least no error message from modprobe

ALSA drivers reinstalled from "fresh" kernel

OK.  What next for a brand new user of Ubuntu?

Thanks.  :p

---

### Post by mostholy on 2007-05-20
Cool that you are looking for help.  I have a Toshiba A135 model and it took some effort to get the sound functional.  What worked for me was to follow the alsa recompile as described here:
[https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000C200_89224MG](https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000C200_89224MG) 
scroll down to the sound portion and follow the step-by-step, it may solve things for you.  

Cheers

---

### Post by jerrynor on 2007-05-20
Thanks.  In reply got the following error message.


/modules/'uname -r'
Password:
depmod: malformed/unrecognized option '-acd'
depmod 3.3-pre2 -- part of module-init-tools
depmod -[aA] [-n -e -v -q -V -r -u]
      [-b basedirectory] [forced_version]
depmod [-n -e -v -q -r -u] [-F kernelsyms] module1.o module2.o ...
If no arguments (except options) are given, "depmod -a" is assumed

depmod will output a dependancy list suitable for the modprobe utility.


Options:
        -a, --all            Probe all modules
        -n, --show           Write the dependency file on stdout only
        -V, --version        Print the release version
        -h, --help           Print this usage message

The following options are useful for people managing distributions:
        -b basedirectory
            --basedir basedirectory    Use an image of a module tree.
        -F kernelsyms
            --filesyms kernelsyms      Use the file instead of the
                                       current kernel symbols.
northwest@northwest-laptop:/lib/modules/2.6.20-15-generic$ sudo tar zxvf ~alsa-hg-hda-intel.tar.gz
tar: ~alsa-hg-hda-intel.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
northwest@northwest-laptop:/lib/modules/2.6.20-15-generic$ 
northwest@northwest-laptop:/lib/modules/2.6.20-15-generic$ cd /lib/modules/`uname -r`
northwest@northwest-laptop:/lib/modules/2.6.20-15-generic$ sudo tar zxvf ~/alsa-hg-hda-intel.tar.gz (or path to downloaded file)
bash: syntax error near unexpected token `('
northwest@northwest-laptop:/lib/modules/2.6.20-15-generic$ sudo depmod -a

---

### Post by jerrynor on 2007-05-20
OK. 

Tried again and I think got the lines right this time.  Down to a patch file

> The patch will have to be downloaded from ALSA bugtrack in a browser it seems. The file required is realtek6.tar.gz (this may have been updated since writing) Heres the[WWW] link.(direct link to file)

Sorry, but I don't know how to put that file some place and the site wants a login which I don't have.

Help!!;););)

---

