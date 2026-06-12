---
title: "Firefox"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by Rich78 on 2007-11-05
Has anyone else had stability issues with Firefox recently?

This evening it's bombed out on me twice and failed to start up again, a reinstallation seems to have stablized it for the time being but just wondered if anyone else has experienced any issue?

Thanks

---

### Post by misfitpierce on 2007-11-05
Firefox has stayed stable for me with adblock extension installed and themes. Not a problem yet... Perhaps you had corrupted cache files or something?

---

### Post by jaybombalous on 2007-11-05
I use ubuntuzilla to keep firefox updated and I have not had a problem yet. I installed one theme and one dictionary pack. I also installed nswrapper so I could run the 32 bit extensions on my 64 bit, that list includes flash player.

Sounds like maybe u should delete ~/.mozilla folder and start over.

---

### Post by por100pre1 on 2007-11-05
Try creating a new profile:

```
firefox -ProfileManager
```

---

### Post by johnwillyums on 2007-11-05
Hi. I'm interested in what jaybombalous says about nswrapper as I'm running 64x Vista and 64x Gutsy as a dual boot and I've had lots of problems with Firefox and flash.

I'm a complete newbie with Ubuntu and Vista and was very pleased to manage to install Ubuntu but then I found that flash inserts on Digg and Stumbleupon sites wouldn't play and neither would dvd.

I took some advice on a thread I started and managed to get my dvd working but still no luck with flash.

I tried all sorts of advice and then got the suggestion that 32bit Firefox would help so I installed that but still no flash except YouTube.

Then I found an install called Swiftweasel , which is basically a 32bit Firefox and have full function with that.

I'm quite happy with Swiftweasel so my question is would there be any advantage to having this nswrapper on my Firefox 64x?

If so what do I do?(baby talk please)

Thanks, John

---

### Post by Billy_McBong on 2007-11-05
[COLOR="Blue"]johnwillyums why cant you just use 64-bit flash?
```
sudo apt-get install flashplugin-nonfree
```

P.S. swiftweasel is not 32-bit firefox, it is a modified version of firefox to run better on your processor(and it is great)[/COLOR]

---

### Post by johnwillyums on 2007-11-05
> **Billy_McBong said:**
> [COLOR="Blue"]johnwillyums why cant you just use 64-bit flash?
```
sudo apt-get install flashplugin-nonfree
```

P.S. swiftweasel is not 32-bit firefox, it is a modified version of firefox to run better on your processor(and it is great)[/COLOR]

Thanks for answering. I already did the above and still no flash.

Anyway Swiftweasel is great so I might as well stick with it. I also got gran paradiso but that doesn't do flash for me either.
Back on Vista I use Opera but they don't do a 64x version yet.

My next task is to find as way of getting my Win Nova DVB-TD tv stick to work but I imagine that's a whole other problem. Cheers, John

---

### Post by jaybombalous on 2007-11-05
for me to get flash to work on 64 bit, first I used ubuntuzilla to d/l and update to the newest version of firefox 2.0.0.9. then I followed this...

1) Download the Plugin and the Viewer from [http://www.gibix.net/dokuwiki/en:raz...spluginwrapper](http://www.gibix.net/dokuwiki/en:raz...spluginwrapper)

2) Install Alien, if not already installed.

to install alien if needed: ```
sudo apt-get install alien
```

3) Convert the downloaded rpm's to deb's (sudo alien -d *.rpm)

4) Install the newly created debs (Install in this order: sudo dpkg -i nspluginwrapper-i386_0.9.90-2_amd64.deb, sudo dpkg -i nspluginwrapper_0.9.90-2_amd64.deb) -- If I got the order wrong, you'll know because it won't install.

5) Download the plugin you want to install, and extract the .so file. For example, to install flash, grab the tar.gz file from Macromedia's website, and extract libflashplayer.so.

6) Move the plugin (example, libflashplayer.so) to /usr/lib/mozilla/plugins. This is where nspluginwrapper stores the main plugin, so it's probably a nice folder to keep them.

7) Now we need nsplugwrapper to make the new plugin, so call: /usr/lib/nspluginwrapper/x86_64/**linux**/npconfig -i /usr/lib/mozilla/plugins/libflashplayer.so (if wanting the flash plugin, of course). Depending on whether or not you run that command with sudo, it will either end up in /usr/lib/mozilla/plugins, or ~/.mozilla/plugins. If you ran it as sudo, you'll need to link it to either your profile's plugins or the main plugins (/usr/lib/mozilla-firefox/plugins). Or copy, doesn't matter. The old plugin must not move, as it's path seems to become hard coded in the new plugin created (which has "npwrapper-" prepended to the old name)


**bold text** : I had to add in another folder for these directions to work, seems the newest nswrapper adds another folder before the actual npconfig file. just do a ```
$cd /usr/lib/nspluginwrapper/x86_64/
$ls
```
and see if there is another folder named linux :)

---

### Post by -grubby on 2007-11-05
Firefox 2 for me is horribly unstable. that's why I use Firefox 3. Funny how an unstable release is more stable than a  stable release (at least for me)

---

### Post by jaybombalous on 2007-11-05
Did u have to compile the source for firefox   3?

---

### Post by daimaru on 2007-11-05
> **Rich78 said:**
> Has anyone else had stability issues with Firefox recently?

This evening it's bombed out on me twice and failed to start up again, a reinstallation seems to have stablized it for the time being but just wondered if anyone else has experienced any issue?

Thanks

hi, 
i had a load of trouble with firefox until recently. crashed a load of times, but i found the problem it was the flash player i installed with the adobe flex 3 beta eclipse plugin. i just had to remove the 
```
~/.mozilla/plugins/libflashplayer.so
```
plugin and then reinstall it , no more crashes since then.

---

