---
title: "File Directory for GIMP"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by Brewsky on 2008-01-06
Trew Newb here...

Need to find the directory for GIMP to install a Scheme Script..  Can anyone help?

Have been a MS geek for so long, this is so new to me....


thanks in advance!


Brewsky

---

### Post by eternicode on 2008-01-06
'tis a hidden directory in your home folder, most likely.  Hidden dirs in linux use a dot (.) in front of the name:

```

user@comp:~$ ls /home/user/.gimp-2.2/
brushes       curves     fonts            gflare          gimpswap.5173  levels   palettes    pluginrc  sessionrc   themerc  tool-options
colorrc       documents  fractalexplorer  gimprc          gradients      menurc   parasiterc  plug-ins  templaterc  themes   toolrc
controllerrc  environ    gfig             gimpressionist  gtkrc          modules  patterns    scripts   templates   tmp      unitrc
user@comp:~$
```

I'm not sure where your scheme script would go, though.

You can also use "ls -a ~" to list all directories (including hidden ones) in your home directory.

---

### Post by Blutack on 2008-01-06
Drop it into .gimp-2.4/scripts
(Click view --> hidden files in nautilus)
Then open gimp, Xtn's, Script-fu, refresh scripts.

---

