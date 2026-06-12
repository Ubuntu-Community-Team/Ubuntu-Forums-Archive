---
title: "I need to remove vm ware server"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by ~~Tito~~ on 2007-10-08
I installed it wrong and I want to remove it so I can install it again. How would I do that?

---

### Post by science4sail on 2007-10-08
try reinstalling with the Live CD

---

### Post by science4sail on 2007-10-08
That should overwrite the existing install

---

### Post by ~~Tito~~ on 2007-10-08
I have nothing to back up with. . . I don't want to lose everything. Any other ways please?

---

### Post by Daishiman on 2007-10-08
If you've install VmWare server from the packages a simple 'sudo apt-get remove vmware-server' should suffice. If you've installed it from the website, the installation directory should contain an uninstall scripts.

---

### Post by ~~Tito~~ on 2007-10-08
Where would they be?

---

### Post by funrider on 2007-10-08
run this in the terminal:

history

you might be able to find the location of the installation file, hence, the uninstall file.

---

### Post by ~~Tito~~ on 2007-10-08
```
  216  cd /desktop
  217  cd /home/tito/Desktop
  218  cd VMware-server-1.0.4-56528.tar.gz
  219  cd vmware-server-distrib
  220  sudo ./vmware-install.pl
  221  vmware
  222  /home/tito/bin/vmware-config.pl.
  223  cd /home/tito/bin/vmware-config.pl.
  224  cd install_flash_player_9_linux
  225  sudo make install
  226  tar -xvzf /home/tito/Desktop/install_flash_player_9_linux.tar.gz
  227  cd install_flash_player_9_linux
  228  ./configure
  229  make
  230  sudo make instal
  231  vmware
  232  /home/tito/bin/vmware-config.pl.
  233  cd /home/tito/bin/vmware-config.pl.
  234  tito@TITOS-LAPTOP:~$ /home/tito/bin/vmware-config.pl.
  235  bash: /home/tito/bin/vmware-config.pl.: No such file or directory
  236  tito@TITOS-LAPTOP:~$ cd /home/tito/bin/vmware-config.pl.
  237  bash: cd: /home/tito/bin/vmware-config.pl.: No such file or directory
  238  tito@TITOS-LAPTOP:~$ 
  239  tito@TITOS-LAPTOP:~$ /home/tito/bin/vmware-config.pl.
  240  bash: /home/tito/bin/vmware-config.pl.: No such file or directory
  241  tito@TITOS-LAPTOP:~$ cd /home/tito/bin/vmware-config.pl.
  242  bash: cd: /home/tito/bin/vmware-config.pl.: No such file or directory
  243  tito@TITOS-LAPTOP:~$ 
  244  cd vmware-server-distrib
  245  sudo vmware-install.pl
  246  $sudo update-rc.d -f vmware-player remove 
  247  sudo delete /etc/vmware/not_configured
  248  rmv
  249  del
  250  vmware
  251  chmod +x /home/tito/bin/vmware-config.pl
  252  sudo chmod +x /home/tito/bin/vmware-config.pl
  253  ./home/tito/bin/vmware-config.pl
  254  sudo apt-get vmware
  255  sudo apt-get remove --purge vmserver_name
  256  history

```

Where would it be? I have way more but I started where the installation started.

---

### Post by ~~Tito~~ on 2007-10-08
FOUND IT!! Thanks guys, will do it again.

---

