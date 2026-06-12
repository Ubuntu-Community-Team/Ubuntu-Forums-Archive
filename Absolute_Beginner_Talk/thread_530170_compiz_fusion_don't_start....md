---
title: "compiz fusion don't start..."
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by sup3roque on 2007-08-20
well

here I'm again, my compiz fusion broke... it work before but now don't start...

when I make compiz --replace &

GConf backend: There is an unsupported value at path /apps/compiz/general/allscreens/options/toggle_window_shaded_key. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/general/allscreens/options/toggle_window_shaded_key. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
inotify_add_watch: No such file or directory
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/switcher/allscreens/options/next_key. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

sup3Roque

---

### Post by sup3roque on 2007-08-20
no one? :S

---

### Post by lyceum on 2007-08-20
Are you sure your graphics card is compatible? How are you loading it? Looks like you are using apt-get install. I just used synaptic package manager. It was easy. I am using Beryl though.

---

### Post by sup3roque on 2007-08-20
Yes, it work before, today don't work... I work whith beryl before the compiz fusion... but today just don't work the fusion...

---

### Post by sailor2001 on 2007-08-20
try this: sudo --replace c- emerald &

---

### Post by sup3roque on 2007-08-20
sup3r@sup3r-laptop:~$ sudo --replace c- emerald &
[1] 14233
sup3r@sup3r-laptop:~$ sudo: please use single character options
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }

[1]+  Exit 1                  sudo --replace c- emerald
sup3r@sup3r-laptop:~$ sudo compiz --replace c- emerald &
[1] 14240
sup3r@sup3r-laptop:~$ Password:


[1]+  Stopped                 sudo compiz --replace c- emerald

---

### Post by sup3roque on 2007-08-20
don't work :S

---

### Post by sailor2001 on 2007-08-20
I assume you have compiz and plug-ins installed (synaptics)  try this: alt/f2  compiz --replace

---

### Post by sailor2001 on 2007-08-20
do you have system/admin/restricted drivers checked?

---

### Post by Nikron on 2007-08-20
Go to the configuration manager and disable the gconf backend.  Or you can rm -R the compiz section of ~/.gconf.  Or if you want to lose all your settings (for almost everything), rm -R ~/.gconf.

---

### Post by sup3roque on 2007-08-20
ok

i go to compizconfig settings manager

i take the default settings and make it works 

thanks all

:)

---

### Post by Gone fishing on 2007-08-20
When I changed from Beryl to Compiz Fusion it wouldn't start until I removed all the previous components (including from the apt cashe) and install all the packages from the same source, it seemed that before I did this I had various components that were incompatible with each other.

---

