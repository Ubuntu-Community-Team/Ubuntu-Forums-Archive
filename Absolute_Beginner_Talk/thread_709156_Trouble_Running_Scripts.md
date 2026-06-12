---
title: "Trouble Running Scripts"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by Gakusei on 2008-02-27
I'm following along the tutorial at [http://linuxcommand.org/wss0030.php]("http://linuxcommand.org/wss0030.php"), but I can't get this script to run. Here is the script:
```

#!/bin/bash

# make_page - A script to produce an HTML file

echo "<HTML>"
echo "<HEAD>"
echo "  <TITLE>"
echo "  The title of your page"
echo "  </TITLE>"
echo "</HEAD>"
echo ""
echo "<BODY>"
echo "  Your page content goes here."
echo "</BODY>"
echo "</HTML>"
```

I have it saved in : /home/(myusername)/bin/make_page

The tutorial says to run it like this:
```
make_page > page.html
```

But all I get is :
```
-bash: make_page: command not found
```

Can anyone tell me what I'm doing wrong?

---

### Post by legend2440 on 2008-02-27
Right click make_page >>properties>>permissions Make sure **execute **box is checked  or else in terminal type ** sudo chmod +x make_page**

If after you make the script executeable it still doesn't work then you probably put the script in a directory that is not in your** PATH**
To check this type  ** echo $PATH **   in the terminal. For example mine returns this:   **/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games**

So to be able to run the script by typing   ** make_page > page.html**    I would copy the script into  **/usr/local/bin** for example

Then in terminal

**make_page > page.html **     should work now

---

### Post by Gakusei on 2008-02-27
Worked perfectly! Thank you very much!

---

### Post by nick_h on 2008-02-27
> If after you make the script executeable it still doesn't work then you probably put the script in a directory that is not in your PATH
Just for information, the default .profile puts ~/bin in the PATH.

---

