---
title: "How do I search files using wildcard in nautilus?"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by snowboard975 on 2007-03-07
I wanted to find all files with extension of txt in nautilus.
So I clicked search button in nautilus and typed in *.txt only to find 0 results although there are many.
Can't I use wildcards such as * in nautilus search?
Or are there any other methods to do such search?

---

### Post by buuntuu! on 2007-03-07
i was having a bad time with nautilus as well when it comes to searching for files, still dont get it!
in gnome you can use >places>search for files, 
it works better.
after getting quite frustrated with nautilus a began using xfe, it doesn't have the looks of nautilus, but it's intuitive.

---

### Post by v8YKxgHe on 2007-03-07
open up Nautilus and press ctrl+s - you can then search from there like *.txt 

Regards,
Alex

---

### Post by snowboard975 on 2007-03-07
> in gnome you can use >places>search for files,
it works better.

> open up Nautilus and press ctrl+s - you can then search from there like *.txt

Thanks a lot!
Both methods are very helpful.

---

### Post by davit on 2008-03-08
Why does Nautilus not respond to root searches.

I used any format of searches but it will not give results.

> sudo -i
> gksudo nautilus
    (places me in /root)
 I point to /  (files system root)

Ctrl s  enter 'hosts'

= NOTHING

Tired this

[PS, I know I should not be using root access]

Ctrl L  '/etc'
Ctrl f  'hosts'
 = nothing

What I believe is does is that Nautilus always starts /chroot into home location and search from this position.

I have put a dummy file 'hosts' in /root

Open Nautilus (as root)
>Ctrl L '/'
>Ctrl F 'hosts'

= /root/hosts

This is not what I expect. I should also get /etc/hosts & /root/hosts.

Any hints anybody

---

### Post by ryanhaigh on 2008-03-16
There are workarounds for this such as the previously mentioned places > find files. You can also install nautilus-search-tool which provides a right click option to search the directory using the places>find files search application. I have also written a howto on recompiling nautilus without tracker support, it is not as hard as it may sound.
[http://ubuntuforums.org/showthread.php?p=4524522](http://ubuntuforums.org/showthread.php?p=4524522)

---

### Post by amidsin on 2008-07-20
> **ryanhaigh said:**
> ... You can also install nautilus-search-tool which provides a right click option to search the directory using the places>find files search application...
[http://ubuntuforums.org/showthread.php?p=4524522](http://ubuntuforums.org/showthread.php?p=4524522)

Could you help with a little guidance on installing nautilus-search-tool in Ubuntu (I'm using Hardy). I could not find repositories or deb packages for it. I have tried installing it from source code, but I could not get though ./configure messages about gconf-2.0:

```

$./configure
...
checking for GCONF... configure: error: Package requirements (gconf-2.0) were not met:

No package 'gconf-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GCONF_CFLAGS
and GCONF_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


```

Thanks

---

### Post by zero-9376 on 2008-07-20
Sorry I cannot assist you with your issue as I am not running Hardy however it is my understanding that Hardy doesn't have tracker search integrated so I don't know how necessary this workaround is.

---

