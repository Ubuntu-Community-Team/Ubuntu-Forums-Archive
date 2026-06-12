---
title: "Madwifi MAKE errors"
date: 2007-05-03
forum: Apple Intel Users
---

### Post by muselive on 2007-05-03
Hi there,

I'm trying to install madwifi, as per the guide located here:

[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

On a Macbook Core 2 Duo 2.00Ghz

After having no luck with madwifi, i tried the ndiswrapper method, alas to no avail. Something about a missing nidiswrapper.ko missing file - anyway, lots of errors along the way there anyway.

So i deided to go back to the madwifi method - After downloading and navigating to the folder through shell, i ran the command, 'make' and 'sudo make' just incase. Im greeted by a torrent of error messages (I cant copy paste due to me not being able to use the internet on that laptop!)

The errors seem very odd - /madwififolder/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory.

There are hundreds of these, but they are probably all connected to this top one, as from my C programming course I vaguely remember that stdio.h is a very fundamental library. Why can't Ubuntu find it? This is really frustrating. There must be a simple fix of this - Ive searched all these forums for similar problems, and found 2 cases, however neither have had an answer.

Any help would be greatly appreciated!
Thanks,
Tom

---

### Post by ronocdh on 2007-05-03
Hm, unfortunate that it isn't working for you. You of course have the build-essential package installed? Do what you can to post the terminal output, as the specific error messages would be a great help in diagnosing the problem.

The fact that you also had problems with ndiswrapper makes it seem like a broader problem.

---

### Post by ronocdh on 2007-05-04
I just ran through widemos's madwifi tips and the first time through I made the careless mistake of not changing directories for the make. Are you sure you've done that? You can graphically navigate to your rot folder and find the madwifi directory that way if you want, and then just type the address after a **cd** command in the terminal.

---

### Post by muselive on 2007-05-04
Hiya, I managed to transfer the terminal output, using my friend's HD5... of all things.
Anyway, here it is.

```
[CODE]tom@tom-macbook:~$ cd Desktop/madwifi-hal-0.9.30.10-r2257-20070410/
tom@tom-macbook:~/Desktop/madwifi-hal-0.9.30.10-r2257-20070410$ ls
ath            COPYRIGHT  kernelversion.c  README      svnversion.h
ath_hal        docs       Makefile         regression  THANKS
ath_rate       hal        Makefile.inc     release.h   tools
BuildCaps.inc  include    net80211         scripts
contrib        INSTALL    patches          SNAPSHOT
tom@tom-macbook:~/Desktop/madwifi-hal-0.9.30.10-r2257-20070410$ sudo make
Password:
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  HOSTCC  /home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode
/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory
/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory
/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory
/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory
/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory
/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory
/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory
/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c: In function 'uudecode_usage':
/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:37: warning: implicit declaration of function 'printf'
/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf'
/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c: At top level:
/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:40: error: expected ')' before '*' token
/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:70: error: expected ')' before '*' token
/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c: In function 'main':
/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:121: error: 'FILE' undeclared (first use in this function)
/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:121: error: (Each undeclared identifier is reported only once
/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:121: error: for each function it appears in.)
/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:121: error: 'src_stream' undeclared (first use in this function)
/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function)
/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:122: error: 'NULL' undeclared (first use in this function)
/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:130: warning: implicit declaration of function 'getopt'
/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:134: error: 'optarg' undeclared (first use in this function)
/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:138: warning: implicit declaration of function 'exit'
/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit'
/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:141: error: 'optind' undeclared (first use in this function)
/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:142: error: 'stdin' undeclared (first use in this function)
/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:144: warning: implicit declaration of function 'fopen'
/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:146: warning: implicit declaration of function 'fprintf'
/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:146: error: 'stderr' undeclared (first use in this function)
/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:147: warning: implicit declaration of function 'strerror'
/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:147: error: 'errno' undeclared (first use in this function)
/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit'
/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit'
/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file'
/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:156: warning: assignment makes pointer from integer without a cast
/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:157: warning: implicit declaration of function 'strncmp'
/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit'
/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:168: warning: implicit declaration of function 'strtoul'
/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:170: warning: implicit declaration of function 'strchr'
/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr'
/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit'
/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:178: warning: implicit declaration of function 'strcmp'
/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:179: error: 'stdout' undeclared (first use in this function)
/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function)
/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function)
/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function)
/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function)
/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:188: warning: implicit declaration of function 'open'
/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function)
/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function)
/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function)
/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:191: warning: implicit declaration of function 'fdopen'
/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit'
/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:199: warning: implicit declaration of function 'read_stduu'
/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode.c:201: warning: implicit declaration of function 'fclose'
make[3]: *** [/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal/uudecode] Error 1
make[2]: *** [/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410/ath_hal] Error 2
make[1]: *** [_module_/home/tom/Desktop/madwifi-hal-0.9.30.10-r2257-20070410] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [modules] Error 2
tom@tom-macbook:~/Desktop/madwifi-hal-0.9.30.10-r2257-20070410$ 


```[/CODE]

Ive also looked for this on the madwifi site, but nothing there either :S

Thanks for your help guys!
Tom

---

### Post by ronocdh on 2007-05-04
I've found [this thread]("http://ubuntuforums.org/showthread.php?t=425592") from a week ago, exact same problem, thread is entirely unresolved.

I personally do not know enough about this to help you out, sorry. You could try to search the repos for that library, but considering very few other people are having this problem, maybe a wipe and reinstall would do you well. 

Just out of curiosity, which wireless chipset are you using? The gentleman in the other thread has a MacBook Pro, Core Duo. He didn't post his wireless chipset, either. I'm going to bump that thread and see whether he's still around.

---

### Post by muselive on 2007-05-04
Hiya,

Ive fixed it. Turns out I botched the install of build essentials, so I went through the synaptics route and installed it that way. It now detects wireless networks, and even connects to unsecured ones, however it is having troubles connecting to our personal WPA network. It just hangs on "waiting for network key"

Anyone know how to get past this?

Thanks,
Tom

---

### Post by ronocdh on 2007-05-04
> **muselive said:**
> Hiya,

Ive fixed it. Turns out I botched the install of build essentials, so I went through the synaptics route and installed it that way. It now detects wireless networks, and even connects to unsecured ones, however it is having troubles connecting to our personal WPA network. It just hangs on "waiting for network key"

Anyone know how to get past this?

Thanks,
Tom
Wonderful, I'm glad it was that simple. From what I've heard WEP is the most reliable connectivity wise, but IIRC widemos was using WPA OK. WPA2 definitely wasn't working, though (IIRC!).

---

### Post by stchman on 2007-05-04
> **muselive said:**
> Hi there,

I'm trying to install madwifi, as per the guide located here:

[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

On a Macbook Core 2 Duo 2.00Ghz

After having no luck with madwifi, i tried the ndiswrapper method, alas to no avail. Something about a missing nidiswrapper.ko missing file - anyway, lots of errors along the way there anyway.

So i deided to go back to the madwifi method - After downloading and navigating to the folder through shell, i ran the command, 'make' and 'sudo make' just incase. Im greeted by a torrent of error messages (I cant copy paste due to me not being able to use the internet on that laptop!)

The errors seem very odd - /madwififolder/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory.

There are hundreds of these, but they are probably all connected to this top one, as from my C programming course I vaguely remember that stdio.h is a very fundamental library. Why can't Ubuntu find it? This is really frustrating. There must be a simple fix of this - Ive searched all these forums for similar problems, and found 2 cases, however neither have had an answer.

Any help would be greatly appreciated!
Thanks,
Tom

Follow my procedure on installing madwifi drivers for Atheros cards:

[http://www.stchman.com/ath_drv.html](http://www.stchman.com/ath_drv.html)

You must have build-essential package installed:

sudo apt-get install build-essential

Hope this helps.

---

