---
title: "flashplayer and opera"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by Jeroen2007 on 2007-02-02
hi every body.

i'm trying to get opera working but what i try opera doesnt like flash

who would be so kind to given some hints to make it work?

i'm sick and tired off firefox

thanks a lot

Greets Jeroen

---

### Post by jordanmthomas on 2007-02-02
Do you have flash installed for firefox?  If not, do that and Opera will pick it up.

If it doesn't, make sure that the path to your flash installation is being searched by Opera.
To find where you have installed flash, try this:
```
sudo find / -iname 'libflashplayer.so'
```
find where it is (likely in some firefox plugin/lib folder) open Opera
Go to Tools -- Preferences and then to the Advanced Tab
Click 'Content' in the left tab and then in the right pane click 'plugin options'

Here is my plugin path...use it as an example, **do not** copy and paste it.  I don't use Ubuntu and I can't assure the libraries are all installed in the same place.
```
/opt/opera/lib/opera/plugins:/opt/netscape/plugins:/usr/lib/nsbrowser/plugins:[COLOR="Red"]/path/to/firefox/plugins[/COLOR]
```

Hope this helps

---

### Post by Jeroen2007 on 2007-02-02
sadly in FF its ok and in Opera not

---

### Post by jordanmthomas on 2007-02-02
Have you tried what I have suggested?

---

### Post by Jeroen2007 on 2007-02-02
yes the plugin finder cant locate the plugin

---

### Post by jordanmthomas on 2007-02-02
interesting....you are sure you have 
```
:/usr/lib/firefox/plugins
``` in the list of directories to search and that there is in fact a libflashplayer.so in there?

If these seem right and it still doesn't work I am not sure what your problem is.  :confused:

---

### Post by Jeroen2007 on 2007-02-04
hi every body,

i'tried and tried pulled my friggin hear out still no flash...
Bummer

---

### Post by Jeroen2007 on 2007-02-04
Solved it....

Adobe does not offer Flash compatabillity with opera...

did uninstall a bit of extensions and my problem with firefox is solved !

thanks for the help

---

### Post by wxnker on 2007-02-04
> Adobe does not offer Flash compatabillity with opera...

Yes it does. Like mentioned in one of the posts above you need to show opera the path to "firefox" plugin directory, if opera does not autodetect it.

This is real simple. Follow jordanmthomas's advice to find out where your firefox plugins are stored. 

In my case in Ubuntu that is : /usr/lib/firefox/plugins

Opera detected this wrong at my system :/usr/lib/mozilla/plugins

In my case I just changed mozilla to firefox, since this is where the plugin is stored at my system.

Again just follow jordanmthomas's advice about how to change the path in opera.

Then click "change path"

Flash works fine. Just remember that Shockwave doesn't. Shockwave does not support linux at all.

---

### Post by Pugwash on 2007-02-08
If you installed opera via automatix , the flash installer doesn't seem to detect it. Uninstall opera through automatix then  Install it through the terminal, then run the flash installer again. It solved the problem for me.

---

### Post by divi on 2007-03-12
I had the  firefox which is fine but java wouldn't work in there ,so I go the latest edition of firefox and still java wouldn't work but flash did on both editions.
So I downloaded opera and java worked straight away but flash didn't so I did what you probley did and went though all the forums relating to opera and flash ,I downloaded one thing and it seemed flash was working but it was the old flash 7, which come with fuzz instead of sound,I have it working now, opera does work with flash somehow,follow his tools commands in opera ,have a few goes at it ,tear your hair out a little more but it is in there somewhere ,I did it and I've only been of Linix for 3 weeks and I'm pretty stupid.

---

### Post by fuscia on 2007-03-12
> **Pugwash said:**
> If you installed opera via automatix , the flash installer doesn't seem to detect it. Uninstall opera through automatix then  Install it through the terminal, then run the flash installer again. It solved the problem for me.

i installed opera through automatix and flash is working fine for me. at the time, i also had swiftfox and swiftfox plugins installed. perhaps the swiftfox plugins would account for my success in that regard.

---

### Post by pmawhorter on 2008-01-17
I was having a similar problem with Ubuntu and Opera, and none of the above fixes worked for me. However,  by adding these three lines to my /usr/bin/opera, I was able to get flash to work:

```

# Flash workaround.
LD_PRELOAD="libflashplayer.so:${LD_PRELOAD}"
export LD_PRELOAD

```

I put them above the comment (which is already in /usr/bin/opera):

```

# Workarounds for the "preloaded libXt" problem.

```

Note: This is a bit of a hack, and I don't recomend trying it until you've exhausted all of the other suggestions from this thread, but it did fix things for me. I had a symlink called "libflashplayer.so" in my /usr/lib/opera/plugins that pointed to a valid libflashplayer.so file. If you're using a different flash plugin, adjust the second line of code (the first non-comment) appropriately (i.e. replace libflashplayer.so in that line with the filename of your plugin). If your plugin file is in another directory and that directory is on your Opera plugins path, this might work, but I don't know whether it will.

-Peter Mawhorter

---

