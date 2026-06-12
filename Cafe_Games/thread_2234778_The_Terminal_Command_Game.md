---
title: "The Terminal Command Game"
date: 2014-07-16
forum: Cafe Games
---

### Post by at_first_light on 2014-07-16
The basic idea is that you can reply with a command in an attempt to keep working. The exact same thing cannot be repeated! For example "cd ~/" can only be used once, but it's okay to use "cd ~/Downloads" because it's not the same. If lots of people post that will become difficult, but check the last few replies at least. If you see some people working up to something for example updating apt , and then the next post installs a program, you can help by perhaps running the program. Alternatively you can also work against them by immediately purging the program. Only 1 command per reply! Have fun! :)

---

### Post by at_first_light on 2014-07-16
```
 wget -c [http://sourceforge.net/projects/synkron/files/synkron/1.6.2/Synkron-1.6.2-src.tar.gz ]("http://sourceforge.net/projects/synkron/files/synkron/1.6.2/Synkron-1.6.2-src.tar.gz")
```

---

### Post by redbikemaster on 2014-07-16
```

tar -zxvf Synkron-1.6.2-src.tar.gz

```

---

### Post by at_first_light on 2014-07-16
```
cd Synkron-1.6.2-src/
```

---

### Post by redbikemaster on 2014-07-16
```

ls

```

---

### Post by at_first_light on 2014-07-16
```
sudo lrelease-qt4 Synkron.pro
```

---

### Post by at_first_light on 2014-07-17
```
sudo qmake-qt4 Synkron.pro
```

---

### Post by at_first_light on 2014-07-17
```
sudo make
```

---

### Post by Metallion on 2014-07-17
sudo rm /etc/sudoers

Disclaimer: ***DON'T*** run this on your system. :p

---

### Post by at_first_light on 2014-07-17
```
echo "that's so evil"
```

---

### Post by at_first_light on 2014-07-17
```

echo "#
# This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaultsenv_reset
Defaultsmail_badpass
Defaultssecure_path=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
rootALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudoALL=(ALL:ALL) ALL

# See sudoers(5) for more information on #include directives:

#includedir /etc/sudoers.d" > sudoers


```

---

### Post by Metallion on 2014-07-17
Sorry mate, you need sudo or root to create that file.

```
su -c "passwd -d root"
```

And now neither are available. ^_^

---

### Post by at_first_light on 2014-07-17
Terminal is still cd'd into the directory ~/Synkron the file sudoers was saved there. You are correct though, it needs to be moved to /etc which requires elevated priviledges.

```

wget http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-amd64.iso

```

---

### Post by Metallion on 2014-07-17
cat /dev/random | sort

---

### Post by at_first_light on 2014-07-17
> **Metallion said:**
> cat /dev/random | sort

And checkmate. The only way I know to stop it would be pressing control z which I can't do since the game only allows typing commands. You sir are never allowed near any of my machines :P

---

### Post by Metallion on 2014-07-18
sorry :) There were these two guys on my shoulder advising me. One of them kept talking about eating porrige with golden spoons and turning his other cheek while the other one discussed his favourite Black Sabbath albums with me. Of course I'd listen to that guy. \m/

But in order to let the game continue we could just log into another tty and call:

```
killall cat
```

Now my cat's secret service agency is monitoring this thread. :(

---

### Post by redbikemaster on 2014-07-18
```

exit

```

---

### Post by Jonathan Precise on 2014-08-08
Back to /dev/pts/1, out of the recently closed tty:

```
sudo -i
<sudo> password for $USER: <password>
```

---

