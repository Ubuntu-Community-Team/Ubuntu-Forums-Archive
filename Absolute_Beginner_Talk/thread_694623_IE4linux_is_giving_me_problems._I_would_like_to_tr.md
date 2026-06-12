---
title: "IE4linux is giving me problems. I would like to try the firefox IE plugin"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by boriquajake on 2008-02-12
I found a script that is designed to get the Firefox IE plugin to work in Linux but I am intimidated. I fear that my nascent linux-fu is nowhere near strong enough to handle even something as basic as a script. Could someone give me a hand?

Here is the script that I pulled from [http://ieview.mozdev.org/ieview-linux.html](http://ieview.mozdev.org/ieview-linux.html) :

> IE View on Linux

IE View is only supported, built for, and tested under Windows. Our user community has stepped up with suggestions for making it work under various Linux setups.

Jonathan Ernst offers setup notes on running IE from Firefox via WINE:

    I reproduced what is made for mozilla on my distribution (gentoo):

       1. put a script in /usr/libexec/iexplore-launcher with the following content:

          #!/bin/bash

          main() {
            wine "c:\program files\Internet Explorer\IEXPLORE.exe" "$@" &
            return 1;
          }

          # Call the main sub, which is defined at the top of this script
          main "$@"

       2.

          put a link in /usr/bin that links to the script:

          ln -s /usr/libexec/iexplore-launcher /usr/bin/iexplore

       3. set /usr/bin/iexplore

---

### Post by hyperair on 2008-02-12
Well, did you do exactly what it said?

---

### Post by boriquajake on 2008-02-12
> **hyperair said:**
> Well, did you do exactly what it said?

No, man, that is the point. I mean look at the first line of the instructions, "put a script in...". I don't know what the heck "put a script" means. How am I going to follow the instruction? I do OK at pasting things into terminal but as soon as the instructions assume a basic knowledge I fall flat on my face.

---

### Post by emarkd on 2008-02-12
All that script does is launch IE in Wine passing it the parameter, which I suppose would be the URL.  There's no integration with Firefox there.  But if you want to try it, no problem.  Just open your text editor and copy the script text you want.  For the first one, it would be:

```
#!/bin/bash

main() {
wine "c:\program files\Internet Explorer\IEXPLORE.exe" "$@" &
return 1;
}

# Call the main sub, which is defined at the top of this script
main "$@"
```

Then save it to you desktop as iexplore-launcher.  Then, from the terminal, move it to the location it wants you to have it:

```
sudo mv Desktop/iexplore-launcher /usr/libexec
```

then make it executable

```
sudo chmod +x /usr/libexec/iexplore-launcher 
```

Then move on to the next command there.  You'll have to use sudo before it, too.

---

### Post by hyperair on 2008-02-12
Hahah, alright. Here goes:

> 1. put a script in /usr/libexec/iexplore-launcher with the following content:

#!/bin/bash

main() {
wine "c:\program files\Internet Explorer\IEXPLORE.exe" "$@" &
return 1;
}

# Call the main sub, which is defined at the top of this script
main "$@"
1.1: Run this command (from your run dialog): ```
gksudo gedit /usr/libexec/iexplore-launcher
```

1.2: Paste this into the text editor window: ```
#!/bin/bash

main() {
wine "c:\program files\Internet Explorer\IEXPLORE.exe" "$@" &
return 1;
}

# Call the main sub, which is defined at the top of this script
main "$@"
```

1.3: Save and close the text editor.

> 2.

put a link in /usr/bin that links to the script:

ln -s /usr/libexec/iexplore-launcher /usr/bin/iexplore
2.1: Run this command in a terminal: ```
sudo ln -s /usr/libexec/iexplore-launcher /usr/bin/iexplore
```

> 3. set /usr/bin/iexplore
3.1: Run this command in a terminal (or run dialog): ```
set /usr/bin/iexplore
```


Hope that helps!

p.s. Terminal can be accessed at Applications->Accessories->Terminal.
p.p.s. Run dialog can be accessed using "Alt+F2" (default key binding).

EDIT: Someone always seems to post before me eh? xD

---

