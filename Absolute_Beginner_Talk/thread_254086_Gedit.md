---
title: "Gedit"
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by shonts on 2006-09-09
As of 2 days ago I am completly new to Ubuntu. I plan on asking alot of questions because I cant seem to find the exact answer Im looking for when I do a search.

1st:
Step by Step, could someone please explain to me how to install gedit.

2nd:
How can I get windows media player files to work through firefox?

3rd:
What book or books are recommended for ubuntu beginners? The easier the transition from Windows the better. Should i just stick with the wiki?

4th:
Is there anything close to adobe flash that I can use in ubuntu for website design?

5th: 
How do I enable viewing of flash files on websites?
___________________________________________________________________________

Thanks for the help everyone. I appreciate it alot!!!!

---

### Post by RobsterUK on 2006-09-09
1 - I'm pretty sure gedit is installed by default. You can find it via Applications > Accessories > Text Editor

2 - To get windows media files to work in general, I would say download [Easy Ubuntu]("http://easyubuntu.freecontrib.org/") it adds several useful things to Ubuntu including windows media support.

3 - Not sure about books, but you should be able to find most info on the forum, wiki or on other sites via a web search.

4 - I don't think you'll find anything similar to Flash/Dreamweaver I'm afraid, but if you have an install file/disc for the windows version you may want to have a look into [Crossover Linux]("http://www.codeweavers.com/products/cxoffice/") which allows you to run windows programs under Linux.

5 - Flash can be installed via the application manager found in Applications > Add/Remove

---

### Post by Angry on 2006-09-09
When I first started (roughly a couple of weeks ago), I found that the [Ubuntu Starter Quide]("http://ubuntuguide.org/wiki/Dapper") was a great source of information.  If anything, it may provide a good base to answer a lot of general questions.

---

### Post by aysiu on 2006-09-09
> **shonts said:**
> 
1st:
Step by Step, could someone please explain to me how to install gedit. Gedit is a text editor. If you have Ubuntu, you already have Gedit installed. If you have Kubuntu, you can use KWrite or Kate--also text editors that come installed. If you're using Xubuntu, you can use Mousepad, which comes installed.

If you're using Kubuntu or Xubuntu and are dying to have Gedit for some strange reason, just paste this command in the terminal: ```
sudo aptitude update && sudo aptitude install gedit
``` Now it's installed.

> 2nd:
How can I get windows media player files to work through firefox? Read this: [http://help.ubuntu.com/community/RestrictedFormats](http://help.ubuntu.com/community/RestrictedFormats)

> 
3rd:
What book or books are recommended for ubuntu beginners? The easier the transition from Windows the better. Should i just stick with the wiki? I've seen only one book for Ubuntu (the novice to professional one), and--while it does have some minor faults--it's an excellent book for someone just starting out.

For websites, I'd highly recommend these:
[http://www.ubuntuguide.org](http://www.ubuntuguide.org)
[http://www.psychocats.net/ubuntu](http://www.psychocats.net/ubuntu) (my own site)
[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)
[http://doc.gwos.org](http://doc.gwos.org)

> 4th:
Is there anything close to adobe flash that I can use in ubuntu for website design? Flash authoring in Linux? Hm. There's something called F4L that you might want to look at.

> 
5th: 
How do I enable viewing of flash files on websites? [http://help.ubuntu.com/community/RestrictedFormats](http://help.ubuntu.com/community/RestrictedFormats)

---

### Post by comppsyco on 2006-09-09
It's more complex, but if you really need flash, you should be able to get it to work in Wine. (the windows API emulator for linux). Also, you can install VMware server edition for free, and I'm assuming that you have a windows install disc, so that should be easy. [http://www.ubuntuforums.org/showthread.php?t=183209](http://www.ubuntuforums.org/showthread.php?t=183209)

---

### Post by aysiu on 2006-09-09
[HOW-TO: Dreamweaver AND Flash 8 Running on Ubuntu Dapper!](http://blog.publicidadpixelada.com/2006/09/04/how-to-dreamweaver-and-flash-8-running-on-ubuntu-dapper/)
[http://f4l.sourceforge.net/](http://f4l.sourceforge.net/)

---

### Post by stig on 2006-09-10
> **shonts said:**
> What book or books are recommended for ubuntu beginners?

I don't know about books for Ubuntu but if you intend using OpenOffice take a look at:

[http://documentation.openoffice.org/manuals/](http://documentation.openoffice.org/manuals/)

---

### Post by airtonix on 2006-10-31
website and flash shouldnt go together..

if your serious about making websites that convey information rather than entertainment then get jiggy with w3c compliant html and ccs and xml and xslt, and to top it off start using pngs and svgs instead of gifs and jpegs.

flash is binary is closedsource is unsearchable, is not information friendly nor multi-platform or multi-device friendly.....and requires you to pay more than $200 to edit the damn things...if you can get the tightarse orange glasses kilt wearing flash designer to give you the source files....

Having said that , i recommend this tookit : 

gimp : bitmap graphics...exports to png, jpg, gif, bmp, ra ,ra ra
inkscape : vector graphics ... exports to png, svg
gedit : edit html, js, xml, xslt, php...feature rich
nautilus : local file borswer, ssh browser, ftp browser
mootools : highly optimised javascrtip librarie for animations, and cool stuff....not convinced? try out the physics demo on their..tada [physics demo page]("http://wiki.mootools.net/demos/physics").
firefox + flock + opera + konqourer + (vmware windoze IE ) : testing grounds. i say vmware coz you can re-produce Internet Explorers bugs more reliably, wine seems to fix some of them.... strangley.

and one final rant >> dont use wysiwyg........because yngwysitpwyiwyg
you-never-get-what-you-see-in-that-piffy-wsyiwyg

---

