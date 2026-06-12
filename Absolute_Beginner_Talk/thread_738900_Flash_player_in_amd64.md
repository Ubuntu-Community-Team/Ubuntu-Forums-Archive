---
title: "Flash player in amd64"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by Nikitas350 on 2008-03-29
Can i install the adobe flash player in amd64 machines? I know about gnash but i want to know if adobe flash is available... Thanks

---

### Post by dcstar on 2008-03-29
> **Nikitas350 said:**
> Can i install the adobe flash player in amd64 machines? I know about gnash but i want to know if adobe flash is available... Thanks

This is answered in the 64-bit forum.

---

### Post by bumanie on 2008-03-29
> sudo apt-get install flashplugin-nonfree nspluginwrapper
I thnik this is the 64 bit adobe flash released about 1 year ago.

---

### Post by Nikitas350 on 2008-03-29
Thanksss

---

### Post by rajeev1204 on 2008-03-29
> **bumanie said:**
> I thnik this is the 64 bit adobe flash released about 1 year ago.

There is no 64 bit flash in existence. the above code just installs a software called nsplugin wrapper which allows flash 32 bit plugin to work in 64 bit browsers.Synaptic downloads and installs the flash plugin and the nspluginwrapper for auto installation. Previously we had to manually install nspluginwrapper then copy flash plugins to firefox directory.

Now its just one click operation :)

---

### Post by Nikitas350 on 2008-03-30
I installed first gnash (to try it) then i removed it through synaptic and then i install adobe flash player from firefox addons. Althogh it is installed, firefox says that i have to download the required addons to view flash files(???)

---

### Post by taavikko on 2008-03-30
if command
```
apt-cache policy flashplugin-nonfree
```
says its installed, try to reconfigure it
```
sudo dpkg-reconfigure flashplugin-nonfree
```

restart browser and test

---

### Post by Nikitas350 on 2008-03-31
--&#921;t doesn't work...--
Update: i fix it using the command "nspluginwrapper -i ~/Desktop/install_flash_player_9_linux/libflashplayer.so"

---

