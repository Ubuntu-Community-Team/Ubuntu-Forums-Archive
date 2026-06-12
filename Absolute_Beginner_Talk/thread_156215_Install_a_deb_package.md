---
title: "Install a deb package"
date: 2006-04-06
forum: Absolute Beginner Talk
---

### Post by elamericano on 2006-04-06
Just when I was getting confident, I ran across a simple task that I don't know how to do. I have a deb package from this web site: [http://klavaro.sourceforge.net/en/index.html](http://klavaro.sourceforge.net/en/index.html)

but I don't know what to do with it. I've looked at the apt-get man page, but apt-get install klavaro_0.9.6-1_i386.deb.bin didn't work. I think it's still looking for it in repositories. So, what's the right command when it's local?

---

### Post by joewhite on 2006-04-06
cd to the directory and then:

dpkg -i debfile

from the console.

---

### Post by KingBahamut on 2006-04-06
sudo ./klavaro_0.9.6-1_i386.deb.bin

sudo dpkg -i klavaro_0.9.6-1_i386.deb

---

### Post by elamericano on 2006-04-06
Thanks guys. I'm not sure what the .bin was for at the end. sudo ./klavaro_0.9.6-1_i386.deb.bin would throw an error, but sudo dpkg -i klavaro_0.9.6-1_i386.deb.bin worked fine.

I've decided that I'd better learn to touch type now that Ubuntu is my primary OS. :KS

Thanks again.

---

### Post by Mustard on 2006-04-06
[QUOTE=elamericano]Thanks guys. I'm not sure what the .bin was for at the end. sudo ./klavaro_0.9.6-1_i386.deb.bin would throw an error, but sudo dpkg -i klavaro_0.9.6-1_i386.deb.bin worked fine.

I've decided that I'd better learn to touch type now that Ubuntu is my primary OS. :KS

Thanks again.[/QUOTE]

A little trick in terminal is to use the TAB key to autocomplete filenames and paths.  This should help with cutting down on typing.  For instance with the .deb file you had above, you could type in the first few letters then hit the TAB key and assuming your terminals working directory is the same as the location of the file, then pressing TAB will autocomplete the name of the file.  This works for file path names too.

---

### Post by lupine_nickt on 2006-04-06
I usually just type enough to make the filename unique, then stick an asterisk (*) on the end. It works for paths as well... so for instance:
'cd /lib/mo*/2.6.15-20*/ker*/sec*' 

is equivalent to 

'cd /lib/modules/2.6.15-20-amd64-generic/kernel/security'

It saves space on the commandline, as well :). I still have MS-DOS nightmares, wherein I've typed a command that wraps over several lines, then realised that there's a typo right at the beginning... heartbreaking, I tell you ;)

</nostalgia>

xF,

...Nick

---

