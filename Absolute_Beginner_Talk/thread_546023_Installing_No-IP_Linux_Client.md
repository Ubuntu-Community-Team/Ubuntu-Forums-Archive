---
title: "Installing No-IP Linux Client"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by Xarok on 2007-09-08
If you know NO-IP.com it allows you to run a server behind a dynamic ip.

You need a program to have their servers be notified when your ip changes.

I've used it on my mac and it works just fine, 
but I am having troubles installing it on my Ubuntu Desktop.

I get a bunch of errors when I try 
'sudo make' and 'sudo make install'. 
Could it be that I don't have a compiler?

Thanks for your help

---

### Post by schorsch on 2007-09-08
You should install some packages to compile from sources:
```
sudo apt-get install build-essential 
```
Perhaps you have to install the kernel headers for your system, too.

---

### Post by hyper_ch on 2007-09-08
(1) get necessary stuff

```

sudo aptitude install build-essential

```

(2) download their .tar.gz file

(3) extract it

```

tar xvfz noip*tar.gz

```

(4) run make

```

cd noip
make

```

(5) install it
```

sudo make install

```

(6) Create startup script
```

sudo nano /etc/init.d/noip.sh

```

(7) Paste this content
```

#! /bin/sh
# . /etc/rc.d/init.d/functions  # uncomment/modify for your killproc
case "$1" in
        start)
                echo "Starting noip2."
                /usr/local/bin/noip2
        ;;
        stop)   
                echo -n "Shutting down noip2."
                killproc -TERM /usr/local/bin/noip2
        ;;
        *)
                echo "Usage: $0 {start|stop}"
                exit 1
esac
exit 0

```

(8) exist and save it by pressing ctrl-x

(9) update the runlevels
```

sudo update-rc.d noip.sh defaults

```

(10) start the script now manually
```

sudo /usr/local/bin/noip2

```

---

### Post by jhyland87 on 2008-04-04
Im trying to install as well, would I see this in the applications menu at all?

---

### Post by hyper_ch on 2008-04-04
you don't have to build the noip client from source anymore. It's meanwhile in the repos, just install the "noip2" package.

It will not appear in the applications menu as it is not a gui program.

---

### Post by superprash2003 on 2008-04-04
you could also install the windows no-ip version through wine.. it works fine

---

### Post by jhyland87 on 2008-04-04
> **superprash2003 said:**
> you could also install the windows no-ip version through wine.. it works fine
True, I just hate using wine for a program that also has a version for linux

---

### Post by jhyland87 on 2008-04-04
> **hyper_ch said:**
> you don't have to build the noip client from source anymore. It's meanwhile in the repos, just install the "noip2" package.

It will not appear in the applications menu as it is not a gui program.

then how do I edit information on it?

---

### Post by aeiah on 2008-04-04
using the config files, probably (they'll be in a hidden folder in your home directory. ".noip2" probably). type noip2 --help and see what you get. or man noip2. or visit the noip site and find out from there.

---

