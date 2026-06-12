---
title: "Possible to install Times New Roman?"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by Kosimo on 2007-10-24
Where are fonts installed on Ubuntu?

Would be technically possible to install new fonts inserting them to the right place?
I'm trying to have Times New Roman in Open Office

---

### Post by ThrobbingBrain66 on 2007-10-24
You can get a bunch of Microsoft fonts (including Times New Roman) by installing the msttcorefonts package.

Otherwise, fonts can be found in /usr/share/fonts

---

### Post by Kosimo on 2007-10-24
Thank you soo much ;)

---

### Post by enigma_0Z on 2007-10-24
There is a package for ubuntu called "corefonts" that will get you all of the M$ fonts (Arial, Times new roman, Comic Sans, etc)...

Google gave me this tutorial (which works)
[http://ubuntu.wordpress.com/2005/09/09/installing-microsoft-fonts/](http://ubuntu.wordpress.com/2005/09/09/installing-microsoft-fonts/)

To do this, however, you have to enable the "universe" repository in Ubuntu. You can probably do that through the package manager.

[edit]
Someone beat me!
[/edit]

[edit 2]
A bit if history, if you are interested...

(taken from the above website)
msttcorefonts has an amusing history; Microsoft licensed the fonts for anyone to freely use (regardless of OS) to help boost the market share of IE. When they won the first browser wars, they removed the files from their site&#8230; but the license says you can freely redistribute them so that&#8217;s how we can legally use them :)
[/edit]

---

### Post by Kosimo on 2007-10-24
My solution was much more easy:

sudo apt-get install msttcorefonts

All problems solved ;)

---

### Post by Kosimo on 2007-10-24
> **enigma_0Z said:**
> There is a package for ubuntu called "corefonts" that will get you all of the M$ fonts (Arial, Times new roman, Comic Sans, etc)...

Google gave me this tutorial (which works)
[http://ubuntu.wordpress.com/2005/09/09/installing-microsoft-fonts/](http://ubuntu.wordpress.com/2005/09/09/installing-microsoft-fonts/)

To do this, however, you have to enable the "universe" repository in Ubuntu. You can probably do that through the package manager.

[edit]
Someone beat me!
[/edit]

[edit 2]
A bit if history, if you are interested...

(taken from the above website)
msttcorefonts has an amusing history; Microsoft licensed the fonts for anyone to freely use (regardless of OS) to help boost the market share of IE. When they won the first browser wars, they removed the files from their site… but the license says you can freely redistribute them so that’s how we can legally use them :)
[/edit]

And now, where are this fonts saved?

---

### Post by hyper_ch on 2007-10-24
```

sudo updatedb

```
--> that can take a little while

```

locate FONTNAME

```

dunno by heart where they are.

---

### Post by enigma_0Z on 2007-10-24
They should show up in openoffice after you:

1. sudo fc-cache -fv

or

2. log out and back in.

They're located at /usr/share/fonts/truetype/msttcorefonts/

---

### Post by por100pre1 on 2007-10-24
You can create a .fonts folder in your user folder:

```
mkdir ~/.fonts
```

and place any .ttf fonts inside it. Log out and log back in and your fonts will be detected.

---

### Post by Kosimo on 2007-10-24
As I said:

I  just installed msttcorefonts  doing sudo apt-get install msttcorefonts 

And everything is installed: I have all fonts I was looking for and this fonts are available in OpenOffice already. So, this is the easier way in my opinion.

---

### Post by Tsar on 2007-10-24
Thanks Kosimo
the sudo apt-get install msttcorefonts

worked ta m8

---

### Post by bluepowder7 on 2007-12-06
thanks!  this solved my issue as well!  it's a silly shame that OpenOffice doesn't automatically load these universal and incredibly popular fonts by default.  at least, the 2.3.0 version didn't.

---

### Post by philinux on 2007-12-06
Found this

> Microsoft released their msttcorefonts set to the public domain years ago. Although you
will no longer find it on a Microsoft website, because it was released
public domain they cannot stop others propogating it. All subsequent
fonts were released under a different licence which is more restrictive

---

### Post by maybeway36 on 2007-12-06
Ubuntu doesn't have them because they're not Free.

---

### Post by Jerry N on 2007-12-06
I just now tried to install msttcorefonts in Gutsy and got a message saying that "Package msttcorefonts is not available.. " and "E: Package msttcorefonts has no installation candidate".

Anyone know what gives?

Jerry

---

### Post by bluepowder7 on 2007-12-06
> **Jerry N said:**
> I just now tried to install msttcorefonts in Gutsy and got a message saying that "Package msttcorefonts is not available.. " and "E: Package msttcorefonts has no installation candidate".

Anyone know what gives?

Jerry

i loaded it today, maybe 9 hours ago, using that apt-get command and it mostly worked fine.  i'm on 7.10, though, so i have my restricted drivers and various repositories enabled.  not sure if 7.04 has or needs the same settings to work.

---

