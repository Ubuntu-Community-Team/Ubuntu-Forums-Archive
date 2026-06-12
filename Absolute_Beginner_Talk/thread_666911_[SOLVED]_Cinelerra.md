---
title: "[SOLVED] Cinelerra"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by Terry N on 2008-01-13
Hello All
Well I got Cinelerra install using the info located here [http://project.akirad.net/node/18](http://project.akirad.net/node/18) but it won't run. When I click on the icon nothing happens?
Any ideas?
Thanks Terry:confused::confused:

---

### Post by Dark Aspect on 2008-01-13
Hm can you load the application under the terminal to get an output?

---

### Post by Terry N on 2008-01-13
I do not know how to do that?  

Thanks for the reply.

Terry N

---

### Post by icechen1 on 2008-01-13
In a terminal run ```
cinelerra
``` and post the output here.

---

### Post by Terry N on 2008-01-13
When I ran it in a terminal a window opened for a split second and then closed again.

Thanks again.

Terry N

---

### Post by icechen1 on 2008-01-13
Do you have compiz enabled,try swiching on and off.It can also cause of bad packages from the site you are trying to install from.If it don't run it might be broken package and you could try installing it from the official ubuntu repos(i am not sure if they have it)

---

### Post by Terry N on 2008-01-13
I am sorry but I do not know what compiz is?

Thanks Terry N

---

### Post by Dark Aspect on 2008-01-13
> **Terry N said:**
> I am sorry but I do not know what compiz is?

Thanks Terry N

Compiz Is a 3D desktop,I don't really think that causing much of a problem but I might be wrong.Does the package have any dependencies?

---

### Post by Terry N on 2008-01-13
Yes and I installed it in the package manager and it supposedly installed them all.

Thanks again, Terry.

---

### Post by akir4d on 2008-01-16
I can help you, but I need some informations...

Have you mixed repository? 
What is your processor? 
Have you try cinelerra or cinelerra-generic? 
Have you gutsy installed?

byez

Paolo Rampino

---

### Post by azad on 2008-01-16
Isn'y Cinerella available in Ubuntu repository? Go to Add/Remove Programs and see if its available. If you do then, remove what you installed from Akirad Repo and install it from Ubuntu repo.

Also turn off Compiz. Right click on desktop > Change desktop background. Click on the Effects tab and change it to "None".

Cheers.

---

### Post by cotcot on 2008-01-16
Although I see that you are new to terminal and compilation I give you the way I got cinelerra.  Maybe you want to give this a try.

I have compiled cinelerra myself to have it with openGL enabled.
This is the way I have done it :

Dependencies to be met before compiling cinelerra

```
sudo apt-get install build-essential automake1.7 libtool xorg-dev libasound2-dev libogg-dev libvorbis-dev libtheora-dev libopenexr-dev libdv4-dev libpng12-dev libjpeg62-dev uuid-dev libmjpegtools-dev liba52-dev liblame-dev libsndfile1-dev libfaac-dev libfaad-devllibfaad2 libfaad0 fftw3-dev libraw1394-dev libavc1394-dev libiec61883-dev libtiff4-dev subversion checkinstall yasm nasm libarts1-mpeglib libmpeg-dev libmpeg1 libmpeg2-4-dev libmpeg3-1 libmpeg3-dev x264

```

Compiling and installing Cinelerra

Get the latest revision of Cinelerra:

```
svn checkout svn://svn.skolelinux.org/cinelerra/trunk/hvirtual
```


cd into the hvirtual folder (in my example /home/username/hvvirtual that was created when downloading to latest revision and edit the autogen.sh file with gedit:

```

cd /home/username/hvvirtual
gedit autogen.sh
```

find this

```
# export AUTOMAKE=/usr/bin/automake-1.7
# export ACLOCAL=/usr/bin/aclocal-1.7
```


and remove the hashes (#) in front of both lines, and save the file.
Now we are going to compile Cinelerra. cd to the hvirtual directory and execute the following commands:
```

./autogen.sh
./configure
make
sudo make install
```



Read carefully the output of the output of the ./configure instruction  to check eventual remaining unmet dependencies.
ESD sound is not required.

Compilation (make) stopped with error. I had to do :

```
touch po/de.gmo
touch po/es.gmo
touch po/sl.gmo
touch po/fr.gmo
touch po/it.gmo
touch po/pt_BR.gmo
touch po/eu.gmo
```


And then restart compilation.

During make I had to install "nasm" to overcome this error :

    .libs/fdct_mmx.o: No such file or directory
    > make[2]: *** [libmpeg2enc.la] Error 1 


The following errors occurred at start of cinelerra:

cinelerra: error while loading shared libraries: libquicktimehv-1.6.0.so.1: cannot open shared object file: No such file or directory
This is when it is a first install. The error can be solved with
```
sudo ldconfig
```
 after make install.


void MWindow::init_shm0: WARNING:/proc/sys/kernel/shmmax is 0x2000000, which is too low.
Before running Cinelerra do the following as root:

For a permanent change, add to the `/etc/sysctl.conf' file the following line:
kernel/shmmax=0x7fffffff

```
sudo su
gedit /etc/sysctl.conf
```

For the first time, to avoid restarting your computer, use the following command as root:
```
sysctl -p
```


And then restart compilation.

---

### Post by Terry N on 2008-01-16
I have added and removed many repositorys. I do not know what you mean by mixed. I am running a AMD 64 processor I am thinking around 2.1 G Hz on a laptop. I installed the I 386 32 bit version of Ubuntu because I read somewhere the 64 bit version may not run programs like wine. I have tried many versions of Cinelerra including both you mentioned and the results are the same. I do nut know what gutsy is but I will see if it is installed. I thank all you guys for your help. I am sorry to be such a pain. I want you to know I have downloaded Linux books and am trying to learn on my own also.

thanks again

Terry N:confused:

---

### Post by akir4d on 2008-01-17
Ok, follow this step:

1 open synaptic from terminal: env LANG=en_US.UTF8 sudo synaptic
2 go to setting>repositories
3 Third-party Software and disable all except akirad and medibuntu
4 close repositories window
5 press reload
6 press Status>Installed (local or obsolete)
7 select first package and press ctrl+e and force to ubuntu (or medibuntu) version ( mark to remove if the package not exist on ubuntu version)
8 repeat this operation to all package on this list
9 press apply
10 find ubuntu-desktop ubuntu-base and install it

Try to start cinelerra

byez

Paolo Rampino aka Akirad

---

### Post by Terry N on 2008-01-17
Man I cannot thank you enough I do not know what you had me do but it worked. I had to find the repositories you listed off the internet by copying and pasting the commands to run in a terminal. Then I followed your instructions to the tee and it worked. :guitar::guitar: Since I posted my reply last night I had updated to Ubuntu Studio and it also works great when booting the Ubuntu 7.10, kernel 2.6.22-14 generic but it added Ubuntu 7.10, kernel 2.6.22.14-RT and that won't boot. Gave me an error the first try that X system or something like that is not configured. Do I need that kernel? I am tickled pink. I really would like to go take classes on linux. It is a challenge but when it works it works great.
I thank you again. Can you tell me how post a thank you on the forum? I will mark it solved:):) 

Thanks again 

Terry N

---

### Post by Terry N on 2008-01-17
PS Should I enable the repositories you had me disable?

Thanks Terry N

---

### Post by akir4d on 2008-01-18
:shock::shock::shock::shock::shock::shock:

---

### Post by akir4d on 2008-01-18
Anyway, for newbe it's a very bad idea to mix debian and ubuntu repository!

---

### Post by Terry N on 2008-01-18
Hello
Your second to last reply did not have any text in it.
I did find the Gutsy repository was install and enabled when correcting this concern. Should it be enable or just leave the two enable you referred me to?
Thanks again Terry

---

### Post by Terry N on 2008-01-18
Hello again,

I found that when trying to boot the Ubuntu 7.10, kernel 2.6.22-14-RT the error something about the X-server when I view it mentions my NVIDA graphcs card and something about no screen found.
Do you know how I could correct this concern. I started a new thread on this issue but no one has replied.

Thanks again, Terry

---

### Post by smkoberg on 2008-01-24
Hey guys, I installed Ubuntu Studio earlier and I've been trying to install Cinelerra to no avail. 

I tried CotCot's method of compiling Cinelerra but I'm getting stuck at the step to actually start compiling. 

after I cd to the hvirtual directory and enter ```
./configure
```
I get
```
bash: ./configure: No such file or directory
```

Up until this point, everything seems to have gone fine.

:confused:

---

### Post by cotcot on 2008-02-07
> **smkoberg said:**
> Hey guys, I installed Ubuntu Studio earlier and I've been trying to install Cinelerra to no avail. 

I tried CotCot's method of compiling Cinelerra but I'm getting stuck at the step to actually start compiling. 

after I cd to the hvirtual directory and enter ```
./configure
```
I get
```
bash: ./configure: No such file or directory
```

Up until this point, everything seems to have gone fine.

:confused:
Sorry, this is my fault. I forgot the line ./autogen.sh in the code I gave.
There is no configure file in the download. It must be generated with ./autogen.sh
I have added the line in my post with the method.

---

### Post by val67 on 2008-02-10
Hi Cotcot,

I also have an AMD 64 3800+. 

The problem is that ubuntu 7.10 (32 bit install) only sees 1 core:

top - 09:12:52 up 18:02,  2 users,  load average: 0.37, 0.30, 0.27
Tasks: 132 total,   1 running, 131 sleeping,   0 stopped,   0 zombie
Cpu(s):  4.7%us,  2.3%sy,  0.0%ni, 93.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1229676k total,  1191792k used,    37884k free,    73200k buffers
Swap:  1454392k total,    62532k used,  1391860k free,   744792k cached

uname -a:
2.6.22-14-generic #1 SMP Fri Feb 1 04:59:50 UTC 2008 i686 GNU/Linux

I have 2 questions:

1. Are you running Cinelerra on Ubuntu 32 or 64 bit?
2. Are both of your cores recognized?

Thanks,

Val

---

### Post by cotcot on 2008-03-17
Sorry for the late reply val67. I running cinelerra on 32 and 64 bit (different OS on the same pc). Both are running on the 2 cores.

---

