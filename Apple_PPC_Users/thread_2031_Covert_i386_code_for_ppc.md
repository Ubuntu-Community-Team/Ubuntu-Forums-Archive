---
title: "Covert i386 code for ppc"
date: 2004-10-25
forum: Apple PPC Users
---

### Post by vj2k on 2004-10-25
Hi,
I am new to the linux world and have just loaded ubuntu to my ibook. I need some specific softwares relating to statistics. One software OPENSTAT ([www.statpages.org/miller/openstat/](www.statpages.org/miller/openstat/) ) has been built for i386, Is it possible to convert the same for ppc. The source code is avaliable. And secondly how can do compile a code in linux. I am sorry if it is naive but I am a newbie to this world. In case anybody knows of any other statistics softwre for linux ppc kindly inform me
vijay

---

### Post by daniels on 2004-10-25
The short answer is 'you can't'; the long answer is 'you can't'.

---

### Post by bakunin74 on 2004-10-25
Converting is not possible.

BUT:

1.) If you have the source-code you can compile the app for ppc. HowTo? The bonsai answer for ca. 90% of cases: download the sourcecode (usually a compressed file) uncompress ist, open a terminal window (under system tools in the apps menu) type

cd <space>

drag the folder that you just have decopressed to the window to avoid typing the full path

that will give you 

cd /home/<username>/<foldername> 

assuming you dl your files directly to your home directory

type 

./configure

something should happen. if no error messages occur type

make

get some rest, whatch a movie ... if no error messages occur type

sudo make install

type your password and whait for a moment. ready

2.) If there are just the binaries for i386 are available get an emulator like QEMU ([http://fabrice.bellard.free.fr/qemu/](http://fabrice.bellard.free.fr/qemu/)), read the how to, ask google and hope the best...

good luck, bak

---

