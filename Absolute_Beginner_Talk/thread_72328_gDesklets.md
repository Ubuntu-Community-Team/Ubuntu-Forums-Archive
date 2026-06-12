---
title: "gDesklets"
date: 2005-10-05
forum: Absolute Beginner Talk
---

### Post by Vega on 2005-10-05
so far so good on my linux set up. I got all my codecs working! ^^ 

Now for a theme change. I downloaded gDesklets and used the "sudo apt-get install gDesklets" command it seemed the terminal gave a postive response while connecting to repositories and downloading packages. When it was done I didn't see it in the applications or themes menu. Can some one guide me as to what I did wrong

thanks -_^

---

### Post by Kyral on 2005-10-05
first off try killall gnome-panel to refresh the panel.

That SHOULD introduce the gDesklets Shell into the menus. After that just go to the Desklets site (unknown off the top of my head) and download + install them :D

---

### Post by Strangerdave on 2005-10-05
you can also try sudo apt-get gdesklets-data 

this, I believe gives you several desklets to play with from the start.

-SD-

---

### Post by Kyral on 2005-10-05
Last I knew the gdesklets-data package was broken.

---

### Post by manicka on 2005-10-05
The data package is broken in hoary, you're better off downlaoding the desklets you need from [http://gdesklets.gnomedesktop.org/](http://gdesklets.gnomedesktop.org/)

---

### Post by Vega on 2005-10-05
[QUOTE=Strangerdave]you can also try sudo apt-get gdesklets-data 

this, I believe gives you several desklets to play with from the start.

-SD-[/QUOTE]

umm.. I got "Invalid operation gdesklets-data"

---

### Post by Strangerdave on 2005-10-05
Sorry, I did not realize that the package was broken.  You should follow the advice of manicka.

-SD-

---

### Post by Vega on 2005-10-06
[QUOTE=manicka]The data package is broken in hoary, you're better off downlaoding the desklets you need from [http://gdesklets.gnomedesktop.org/](http://gdesklets.gnomedesktop.org/)[/QUOTE]

 my browser times out when trying to download it.

---

### Post by Mustard on 2005-10-06
I just checked the URL in my browser.  It loaded up ok.  Not sure what the issue is on your end.

---

### Post by Vega on 2005-10-06
[QUOTE=Mustard]I just checked the URL in my browser.  It loaded up ok.  Not sure what the issue is on your end.[/QUOTE]
I should of been more clear the download gDesklets-0.35.2.tar.bz2 won't ask me to download which means it's broken.

---

### Post by manicka on 2005-10-06
[QUOTE=Vega]I should of been more clear the download gDesklets-0.35.2.tar.bz2 won't ask me to download which means it's broken.[/QUOTE]
If you already have gdesklets installed with apt you don't need it again. It's only the data paclkage that is broken. 
Once it's up and running you can add individual desklets that you downlaod from the gdesklets site.

---

### Post by Vega on 2005-10-06
[QUOTE=manicka]If you already have gdesklets installed with apt you don't need it again. It's only the data paclkage that is broken. 
Once it's up and running you can add individual desklets that you downlaod from the gdesklets site.[/QUOTE]
this means that I should wait for it be back.

---

### Post by Vega on 2005-10-06
this means that I should wait for it to come back.

sorry for double post

---

### Post by manicka on 2005-10-06
[QUOTE=Vega]this means that I should wait for it be back.[/QUOTE]

Maybe I should be clearer.

Install the gdesklets package with synaptic or with apt 'sudo apt-get install gdesklets'.

Don't install the gdesklets-data datapackage. I you have, remove it.

Go to [http://gdesklets.gnomedesktop.org/](http://gdesklets.gnomedesktop.org/) and download the desklets you need.

To be safe and to get rid of old config files, remove the .gdesklets folder in your home directory. If you don't see that folder it in nautilus use ctrl-H to unhide it.

Start the gdesklets shell. Applications -->Accessories --> gDesklets

Install the downloaded desklets by using File--> Install package in the gDeskets shell. You'll then see the desklet you installed in the window.

Highlight the installed package then, File--> Run selected desklet

HTH :)

---

### Post by Vega on 2005-10-06
problem solved!

P.S If we all work on trouble shooting at this rate wintel users will have no excuse! lol

---

