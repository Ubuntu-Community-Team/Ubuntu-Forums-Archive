---
title: "Firefox not recognising Java plugin"
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by ekke on 2006-03-19
I have downloaded and installed Jre1.5.06 and installed it according to the instructions on the Sun website. I have to link it to Firefox in the "plugins" directory in the firefox directory, but there is no such directory. I made a plugins directory in /etc/mozilla-firefox/ and linked to the appropriate file in the java directory, but Firefox is still not recognising the plugin. Any help?

---

### Post by joshuapurcell on 2006-03-19
Here's what my plugins directory has in relation to Java:```
joshua@jlpurcell:/opt/firefox/plugins$ ls -l *java*
lrwxrwxrwx  1 root root 57 2006-01-03 23:40 libjavaplugin_oji.so -> /usr/lib/j2re1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so
```
As you can see, my plugins directory is located in **/opt/firefox/plugins**. Your directory may be different than this, but the actual symbolic link you need to create is most likely to the same file as above. You can possibly find your already existing plugins directory by doing this:```
sudo updatedb
sudo locate libnullplugin.so
```This will first update your files database (so you can search through them), then the second line searches through your files for one that should already be located in the plugins directory of Firefox after being installed. Once you find that file, do another search for libjavaplugin_oji.so. After that, navigate to the directory where libnullplugin.so is and create a symbolic link to libjavaplugin_oji.so like this:```
sudo ln -s /usr/lib/j2re1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so ./libjavaplugin_oji.so
```

---

