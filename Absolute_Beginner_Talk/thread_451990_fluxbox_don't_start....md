---
title: "fluxbox don't start..."
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by gustavocm on 2007-05-22
Hi,

i installed fluxbox from the repository, but it don't start.
I select fluxbox in the login window, enter my password and get a gray screen (my login window background color) and it stays in this screen.

someone had seen something similar to this? 
thank you.

---

### Post by taurus on 2007-05-22
I think that is what you get as a default fluxbox.  What happens if you click the right button to bring up the menu?

---

### Post by gustavocm on 2007-05-22
the menu doesn't appear....
fluxbox has a splash screen like gnome?

---

### Post by gustavocm on 2007-05-23
I tried to compile fluxbox before getting it from the repo. I got an error in the compiled fluxbox. tried to uninstall it doing **sudo make uninstall**. got this:

```
make[3]: Entering directory `/home/odin/fluxbox-1.0rc3/data/styles'
rmdir /usr/local/share/fluxbox/styles
rmdir: /usr/local/share/fluxbox/styles: Directory not empty
make[3]: *** [uninstall-local] Error 1
make[3]: Leaving directory `/home/odin/fluxbox-1.0rc3/data/styles'
make[2]: *** [uninstall-recursive] Error 1
make[2]: Leaving directory `/home/odin/fluxbox-1.0rc3/data/styles'
make[1]: *** [uninstall-recursive] Error 1
make[1]: Leaving directory `/home/odin/fluxbox-1.0rc3/data'
make: *** [uninstall-recursive] Error 1

```

And installed from the repo, and now i have the error i said.
maybe i have to completely remove the compiled fluxbox? but how i do this?

---

### Post by RedSquirrel on 2007-05-24
When you compiled fluxbox, if you did not specify a different installation prefix, the program files are in /usr/local/bin.

On the other hand, the fluxbox package from the repositiories installs the files in /usr/bin.

I would check your /usr/share/xsessions/flubox.desktop file. For the version from the repositories, it should look like this:

```
[Desktop Entry]
Encoding=UTF-8
Name=Fluxbox
Comment=Highly configurable and low resource X11 Window manager
Exec=/usr/bin/startfluxbox
Terminal=False
TryExec=/usr/bin/startfluxbox
Type=Application

```Have a look in /usr/local/bin to see if the files you don't want have been removed:

For example:

/usr/local/bin/fluxbox
/usr/local/bin/fluxbox-update_configs
/usr/local/bin/fluxbox-generate_menu
/usr/local/bin/startfluxbox
/usr/local/bin/fbrun
/usr/local/bin/fbsetbg
/usr/local/bin/fbsetroot


You can check exactly what the "sudo make install" command installed by creating a log file like this:

```

make -n install | tee install_log-`date +%F-%T`

```By the way, when you want to use a version of Fluxbox that you compiled yourself, I would recommend using **checkinstall** to build a deb and then install that rather than using "sudo make install". It makes it so much easier to install/uninstall.

What error did you have with the compiled version? Just curious. :)

---

### Post by gustavocm on 2007-05-24
i installed now the fluxbox with the compiled way using the tuto:
[http://ubuntuforums.org/showthread.php?t=116759](http://ubuntuforums.org/showthread.php?t=116759)

and now it works.
The last time i tried to install the compilled fluxbox I was having a permission problem , but i didn't realize that. Now i just did a **chmod a+x** on the startup script and the fluxbox works fine.

but the fluxbox i installed via synaptic didn't work, the **/usr/share/xsessions/flubox.desktop** is exactly the same as yours and i removed those files. Maybe i was not waiting for that slow startup that is fixed with the **./configure --disable-xmb**.

Thank you!

---

### Post by RedSquirrel on 2007-05-24
> **gustavocm said:**
> i installed now the fluxbox with the compiled way using the tuto:
[http://ubuntuforums.org/showthread.php?t=116759](http://ubuntuforums.org/showthread.php?t=116759)

and now it works.
The last time i tried to install the compilled fluxbox I was having a permission problem , but i didn't realize that. Now i just did a **chmod a+x** on the startup script and the fluxbox works fine.

Great. :)

> **gustavocm said:**
>  but the fluxbox i installed via synaptic didn't work, the **/usr/share/xsessions/flubox.desktop** is exactly the same as yours and i removed those files. Maybe i was not waiting for that slow startup that is fixed with the **./configure --disable-xmb**.

No, that's no longer an issue. That tutorial is rather old and it has not been updated in over a year. Things have changed since then. These days, the default configure settings work just fine.

I'm not sure why the version from the repositories didn't work for you. It's probably safest to rename your ~/.fluxbox directory to something else before installing that version, just so the installer has a chance to create a "fresh" .fluxbox directory. Perhaps your permission issue was causing a problem for the version from the repositories too. :confused:

Oh well, all of this is moot now that you have a working version. Enjoy! :)

---

