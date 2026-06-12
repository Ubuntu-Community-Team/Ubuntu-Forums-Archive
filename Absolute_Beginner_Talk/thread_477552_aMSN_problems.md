---
title: "aMSN problems"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by ajmannen on 2007-06-18
Hi, when i try to log into aMSN with my msn acount i get this [[img]http://bildr.no/thumb/77782.jpeg[/img]](http://bildr.no/view/77782)
I choose linux_86, and get this [[img]http://bildr.no/thumb/77783.jpeg[/img]](http://bildr.no/view/77783)

I run Ubuntu 7.04 32 bit, plz help

---

### Post by Jimmyfj on 2007-06-18
This is because you have downloaded the wrong version of aMSN, you'd 0.96 instead of 0.97

---

### Post by ajmannen on 2007-06-18
But i used Add/remove programs...

---

### Post by ajmannen on 2007-06-18
Ok, i re-installed aMSN but still get the same error :(

---

### Post by rikbrown2k on 2007-06-18
Hey, I had this problem too, seems to be some issue with aMSN.
The solution I found worked was to download and install tls manually:

Download the tls module
```
wget http://dfn.dl.sourceforge.net/sourceforge/tls/tls1.5.0-linux-x86.tar.gz
```

Extract the files in the archive
```
tar xvf tls-1.5.0-linux-x86.tar.gz
```

Then copy the tls into the usr/lib folder
```
sudo cp -r tls1.5.0 /usr/lib
```

try this :)

---

### Post by ajmannen on 2007-06-18
[[img]http://bildr.no/thumb/77811.jpeg[/img]](http://bildr.no/view/77811)

Umm...

---

### Post by rikbrown2k on 2007-06-18
Seems it saved the archive with a ".3" on the end, hopefully it's still fine... just do 
```
tar xvf tls-1.5.0-linux-x86.tar.gz.3
``` instead.

(tar xvf is the tool to extract the files from the archive name specified after).

If it doesn't work for some reason - maybe it's a bad download, start again, except replace all the occurances of the previous link with this other mirror:
```
http://kent.dl.sourceforge.net/sourceforge/amsn/tls-1.5.0-linux-x86.tar.gz
```

say how this goes :)

---

### Post by ajmannen on 2007-06-18
How it goes, well 
[[img]http://bildr.no/thumb/77819.jpeg[/img]](http://bildr.no/view/77819)

---

### Post by rikbrown2k on 2007-06-18
ah sorry, think you got the wrong end of the stick, heh,  I meant to run the previous commands again but substituting in the new URL.  Lessstart again.


Oke, delete any files the previous messing around in the folder made, and run these updated commands.

```
wget http://kent.dl.sourceforge.net/sourceforge/amsn/tls-1.5.0-linux-x86.tar.gz
tar xvf tls-1.5.0-linux-x86.tar.gz
sudo cp -r tls1.5.0 /usr/lib
```

Pay attention to the output of the wget command when you run it, notable the last line, for example:
19:09:55 (125.85 KB/s) - `**_tls1.5.0-linux-x86.tar.gz_**' saved [17490/17490]
If your command outputs something different to this, then adjust the second line of code (starting with tar xvf) so it has this filename at the end, instead of what I wrote.

---

### Post by ajmannen on 2007-06-18
[[img]http://bildr.no/thumb/77832.jpeg[/img]](http://bildr.no/view/77832)

Hope i'm not being to stupid;)

---

### Post by zachalekos on 2007-06-18
[http://ubuntuforums.org/showpost.php?p=1091856&postcount=4](http://ubuntuforums.org/showpost.php?p=1091856&postcount=4)
try that. it worked for me

---

### Post by rikbrown2k on 2007-06-18
My bad in writing the first code, looks like the files in the archive were extracted into a folder called tls1.50, as you can see by your output  from the tar program:
```
tls1.50/
tls1.50/pkgIndex.tcl
tls1.50/tls.tcl
tls1.50/libtls1.50.so
```

So all you need to do now is change the "cp" line so it reads 
```
sudo cp -r tls1.50 /usr/lib
```

Just run that last line again as above, no need to download again.

---

### Post by Ko-Pe on 2007-06-18
Hi, i kind of have the same problem...
Dunno if this should go here or elsewhere......anyway
I'm on feisty amd64, I have downloaded and compiled amsn, no problem with that, but when I try to conect it all goes to hell, like damm....k, not that much, says that I need tls blah blah.
I change the pkgindex from 1.5 to 1.50,  but it doesn't work. so I download the source of tls1,50 and try to compile, but it gives me this error and I don't get how to solve it

```
kope@kope:/Personal/dwnld/tls1.5$ ./configure 
creating cache ./config.cache
configure: error: bad ssl-dir: cannot find openssl/opensslv.h under /usr/local/ssl/include

```


any help?

---

### Post by rikbrown2k on 2007-06-18
Afaik you don't need to compile the source (i don't remember doing it!) - if changing the index like the previous poster mentioned (and rerunning AMSN ofc) doesn't work, try the commands I've been explaining.

---

### Post by Ko-Pe on 2007-06-18
if u mean that i should download a precompiled version of tls1,50 and create the tls1.50 dir, it din't work......I tryed using tls1.5.0-linux-x86 and tls1.5.0-linux-x86_64....none work, i didn't just created the dir, and copy the files, after that I did chancge the direction of the tls lib in the preferences, and still none.
I'm compiling for the third time amsn :OP, maybe this is the right time.
any other idea??, plzzzzzz:O)

Sorry about my grammar and all of that, English isn't my native tounge and I don't practice to much :OP

---

### Post by oerd on 2007-06-19
i have more or less the same problem. i think amsn expects tls1.5.0 while what we get from sf.net is extracted as 1.5 without the trailing .0
there has to be a workaround in some configuration file of tls.
i'll get back as soon as i find out...

---

### Post by oerd on 2007-06-19
Actually, the gnutls package that you have installed (with tcltls eventually) should be enough. The problem lies somewhere in the amsn requirements which expect tls1.50 instead of tls1.5.0 (which of course is the same as 1.5)

What I did is edit /usr/lib/tls1.50/pkgIndex.tcl 
```
gksudo gedit /usr/lib/tls1.50/pkgIndex.tcl
```
or (for those familiar with vim):
```
sudo vim /usr/lib/tls1.50/pkgIndex.tcl
```
it should look like:
```

# pkgIndex.tcl - 
#
#    A new manually generated "pkgIndex.tcl" file for tls to
#    replace the original which didn't include the commands from "tls.tcl".
#

package ifneeded tls 1.50 "[list load [file join $dir .. libtls1.50.so] ] ; [list source [file join $dir tls.tcl] ]"

```
The only change is in the last line. **1.5** should be changed into **1.50**. This might be due to a typo in the sources somwhere :D
That's all folks. It should do the trick.

---

### Post by anarchist_hippy on 2007-06-19
Hi, 

I've same problem here. But I solve this with package manager. I install TLS from there, and restart ubuntu & amsn... It's there :)

---

### Post by Jakey on 2007-06-19
**AMSN 0.97RC1 INSTALL / TLS ISSUE RESOLVED:**

I am using Fiesty Fawn and have installed the newest version of AMSN which has a TLS issue. I've read most of the problems pertaining to the TLS issue and have tried just about everything in regards to the TLS problem without much luck.

After testing different things I have resolved the issue and hopefully it will help you resolve yours.

If you've already downloaded the tls manually via wget and copied the folder tls1.5 to /usr/lib and made a symlink to ~/.amsn/plugins and it does not work for you then please undo those steps by doing the following:

```

rm -rf ~/.amsn/plugins/tls1.5 

or 

rm -rf ~/.amsn/plugins/tls1.50 (If you've changed the folder name)

**AND**

sudo rm -rf /usr/lib/tls1.5/

or

sudo rm -rf /usr/lib/tls1.50/ (If you've renamed the folder)

```

Now we need to make sure that tls is completely removed from our system by running the following command:
```

sudo apt-get remove tcltls 

```

Now we are certain that all tcltls has been removed from our system entirely and AMSN is still installed and still requires tls. So let's reinstall tcltls:

```

sudo apt-get install tcltls

```

This will install the new tls1.5.0-4 into /usr/lib/tls.1.50/

Now we create a symlink to make sure we've got all the basis covered and then edit the pkgIndex.tcl by doing the following:

```

ln -s /usr/lib/tls1.50/ /usr/local/lib/ (makes a symlink)

sudo pico /usr/lib/tls1.50/pkgIndex.tcl and add a '0' to the end of 1.5 so that the line reads as follows:
[b]
package ifneeded [color=red]tls 1.50[/color] "[list load [file join $dir .. libtls1.50.so] ] ; [list source [file join $dir tls.tcl] ]"
[/b]

```

Once that's complete, exit your editor and **THAT** should be it! 

Restart AMSN and login and it should work for you. 

These are the exact steps that I took to make my AMSN 0.97RC1 work! I hope it helps you!

---

### Post by oerd on 2007-06-20
I was ok just by editing tls 1.5 to 1.50
to each his own :)

---

### Post by Praill on 2007-09-24
Jakey's instructions were the difinitive answer for me. Simply changing pkgIndex file didn't do it. I had to physically remove all files and sym links and recreate proper ones.
I, most likely, had a butchered up system tho from literally months of trying to get anti-aliased fonts in amsn. I FINALLY did tho!!! WOOHOO!!

Thanks a million Jakey.

---

