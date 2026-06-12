---
title: "Gimp plug-in"
date: 2009-01-18
forum: Art &amp; Design
---

### Post by Joe_Linux on 2009-01-18
I want to install a Gimp plugin CDlabel2.scm from this page [http://www.shallowsky.com/software/cdplugins/](http://www.shallowsky.com/software/cdplugins/). The instructions say to: To install, just save CDlabel.scm to ~/.gimp-version/scripts/CDlabel.scm (im my case I wouuld use CDlabel2.scm because I have Gimp 2.4.5 in Hardy Heron. 
When I try do the above I get this 
joe52@joe52-desktop:~$ gedit ~/.gimp-2.0/scripts/CDlabel.scm

** (gedit:6990): WARNING **: Hit unhandled case 1 (File not found) in gedit_unrecoverable_saving_error_message_area_new.
joe52@joe52-desktop:~$ 

Any help would be appreciated Joe

---

### Post by 73ckn797 on 2009-01-18
> **Joe_Linux said:**
> I want to install a Gimp plugin CDlabel2.scm from this page [http://www.shallowsky.com/software/cdplugins/](http://www.shallowsky.com/software/cdplugins/). The instructions say to: To install, just save CDlabel.scm to ~/.gimp-version/scripts/CDlabel.scm (im my case I wouuld use CDlabel2.scm because I have Gimp 2.4.5 in Hardy Heron. 
When I try do the above I get this 
joe52@joe52-desktop:~$ gedit ~/.gimp-2.0/scripts/CDlabel.scm

** (gedit:6990): WARNING **: Hit unhandled case 1 (File not found) in gedit_unrecoverable_saving_error_message_area_new.
joe52@joe52-desktop:~$ 

Any help would be appreciated Joe

Ignore this

---

### Post by -yay- on 2009-01-19
gedit ~/.gimp-2.0/scripts/CDlabel.scm

shouldn't that be:

gedit ~/.gimp-2.4/scripts/CDlabel.scm



You can also install the script by just clicking and dragging it into the .gimp-2.4/scripts folder inside your home folder. The gimp-2.4 folder is invisible though so you have to press Ctrl-H first to see it.

---

### Post by jrusso2 on 2009-01-19
> **-yay- said:**
> gedit ~/.gimp-2.0/scripts/CDlabel.scm

shouldn't that be:

gedit ~/.gimp-2.4/scripts/CDlabel.scm



You can also install the script by just clicking and dragging it into the .gimp-2.4/scripts folder inside your home folder. The gimp-2.4 folder is invisible though so you have to press Ctrl-H first to see it.

Yes maybe you had Gimp another version of GIMP installed before and it left the settings.

---

