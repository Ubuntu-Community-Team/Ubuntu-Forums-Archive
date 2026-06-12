---
title: "problems installing xchat"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by Sir Noob on 2006-12-03
Yesterday I installed Ubuntu (and Linux for that matter) for the first time.  I did a duel boot.  I installed Xchat from the Applications>Add/Remove Applications menu and it worked great.

Today I decieded to make this a straight Ubuntu machine and read did my partitions and installed it.

Now it won't let me install Xchat with the above method, it says:
*"Xchat IRC cannot be installed on y our computer type (I386) Either the application requires special hardware features or the vendor decieded to not support your computer type"*

Next I tried entering "sudo apt-get install xchat" in a command line, I get the following message
[I]"Package xchat is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xchat has no installation candidate"[/I]


So I tried to build it myself.  I downloaded   xchat-2.6.8.tar.bz2  and saved it to /home/sirnoob/test/ then extracted it (tar xjfv xchat-2.6.8.tar.bz2) then  went to the folder /home/sirnoob/ttest/xchat-2.6.8/ and entered "./configure" I got the following message:
[I]checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.[/I]

Below is the config.log:
[I]hostname = marvin
uname -m = i686
uname -r = 2.6.17-10-generic
uname -s = Linux
uname -v = #2 SMP Fri Oct 13 18:45:35 UTC 2006

/usr/bin/uname -p = unknown
/bin/uname -X     = unknown

/bin/arch              = i686
/usr/bin/arch -k       = unknown[/I]


At this point I don't know what to do next, any ideas?

Thanks
Sir Noob

---

### Post by kebes on 2006-12-03
I would go back to the "sudo apt-get" (or "sudo aptitude") stage and try a few things before trying to build it from source. First, did you enable the extra repositories in your install?
```

$ sudo nano /etc/apt/sources.list

```

Uncomment the lines for "deb universe" and "deb multiverse". (It's also possible, during your reinstall, that they are all commented out because your network connection was down during the second install. In that case be sure to un-comment (remove the #) from the "main" and "updates" and "security" lines also).

Then try again:
```

$ sudo aptitude update
$ sudo aptitude install xchat

```


If that still doesn't work, you could also try manually installing the .deb (again, instead of compiling!). It looks like you can download it from:
[http://www.xchat.org/download/](http://www.xchat.org/download/)

Which appears to want you to download it from:
[http://seerofsouls.com/dists/dapper/contrib/binary-i386/xchat_2.6.8-1ubuntu1_i386.deb](http://seerofsouls.com/dists/dapper/contrib/binary-i386/xchat_2.6.8-1ubuntu1_i386.deb)

To manually install a ".deb" you use "dpkg":
```

$ sudo dpkg -i xchat_2.6.8-1ubuntu1_i386.deb

```

Hope that helps.

---

### Post by Sir Noob on 2006-12-03
Well good and bad news.

Well I tried what you said, I ran into lots of problems, but after I restarted the machine low and behold xchat appeared in my applications>internet menu!  But it wouldn't execute!

I went back through the steps you said and when I preformed 

```
sudo aptitude install xchat
```

it offered to downgrade the package, I told it yes and now it works just fine!

I'm such a noob I have no idea what happened but thanks for pointing me in the more or less right direction!

Sir Noob

---

