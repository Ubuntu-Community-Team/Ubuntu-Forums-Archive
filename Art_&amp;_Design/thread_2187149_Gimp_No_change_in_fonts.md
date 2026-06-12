---
title: "Gimp: No change in fonts"
date: 2013-11-11
forum: Art &amp; Design
---

### Post by dannymichel on 2013-11-11
is it normal for no changes when changing hinting on fonts in gimp [http://d.pr/v/2Bsc](http://d.pr/v/2Bsc) ?

---

### Post by dannymichel on 2013-11-11
I found out it's because I turned hinting off in ~/.fonts.conf. Any way to fix this while still having hinting off in that file? I need that file for Chrome to obey my 'no hinting'.

---

### Post by SeijiSensei on 2013-11-11
Use a script to launch each program that selects the correct configuration.

Create two copies of fonts.conf in your home directory, one with hinting and one without.  Let's call them fonts-hinting.conf and fonts-nohinting.conf.  Then write a script to launch GIMP with hinting enabled that looks something like this:

```

#!/bin/bash

# launch GIMP with font hinting enabled
cd ~
rm -f .fonts.conf
ln -s fonts-hinting.conf .fonts.conf
gimp-2.8 $1
exit 0

```

The script for Chrome would look identical except that the symbolic link would use fonts-nohinting.conf instead.

Become the root user with sudo and place the scripts in /usr/local/bin.  Mark both of them world-executable with "chmod a+x".  If you want them to run from the menus, you'll need to edit the launchers to run the scripts rather than the programs themselves.

---

### Post by dannymichel on 2013-11-11
Thank you. will i have to do this with every app that might want to use hinting, or is it just Gimp?

---

### Post by SeijiSensei on 2013-11-11
Well if you only want to disable hinting in Chrome, then I'd make the default be hinting and just set up a script to reconfigure for Chrome.  I don't use that myself, so I'm guessing about what the binary executable might be called, so let's just say it is called "chrome".

```

#!/bin/bash

# turn off hinting in Chrome only
cd ~
rm -f .fonts.conf
ln -s fonts-nohinting.conf .fonts.conf
chrome $1

# restore hinting when done
rm -f .fonts.conf
ln -s fonts-hinting.conf .fonts.conf

exit 0

```

---

### Post by dannymichel on 2013-11-12
so just make a file called ~/Desktop/script.sh 
and do 
```
#!/bin/bash

# turn off hinting in Chrome only
cd ~
rm -f .fonts.conf
ln -s fonts-nohinting.conf .fonts.conf
chromium-browser $1

# restore hinting when done
rm -f .fonts.conf
ln -s fonts-hinting.conf .fonts.conf

exit 0
```?

---

### Post by SeijiSensei on 2013-11-13
Danny, isn't that exactly the same as my script with chromium as the browser?  You said you were using Chrome which is the branded Google version.  If you are using chromium, then yes, that is the correct script.

---

