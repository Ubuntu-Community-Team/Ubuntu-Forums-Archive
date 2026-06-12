---
title: "keyboard help take #2"
date: 2011-10-31
forum: Apple Hardware Users
---

### Post by giguere56@gmail.com on 2011-10-31
**keyboard problem** 			
 			 			 		   		 		 		here goes:

I cannot get the arrow keys to work... all of them: left, right, up and down.

I am running ubuntu 10.04 on a powerbook G4 model number A1095:
[http://www.everymac.com/systems/appl...g4_1.5_15.html]("http://www.everymac.com/systems/apple/powerbook_g4/stats/powerbook_g4_1.5_15.html")

When i look at the keyboard preference it says USA Macintosh. Further  down that keyboard preference window it says that my keyboard model is:

Generic 105 key ( intl ) PC.

Also the only way I can get the touchpad working is to go to the Terminal everytime I start the laptop and type:

sudo trackpad tap 

and 

sudo trackpad drag.

Is there a way to make this permanent?

Thanks

---

### Post by rsavage on 2011-11-04
Hi, I'm sorry that nobody has replied to your 2 posts about this.
 
I don't own a powerbook so can't give you detailed advice I'm afraid.  Have you tried clicking "Generic 105 key ( intl ) PC." and changing to one of the options that comes up?
 
Your trackapd is unusual in that most posts on this want to disable it rather than enable it!  Have you always had this problem?  Do you have an external mouse plugged in?
 
There are a few ways you can adjust the trackpad permanently I think.  The easy way I think would be to install powerprefs.  At a terminal type:
 
sudo apt-get install powerprefs
 
Then launch it by typing "powerprefs".  I can't remember if you have to have root privileges, in which case you would type:
 
gksudo powerprefs
 
For more guidance on other stuff have a look here [http://ubuntuforums.org/showpost.php?p=11020435&postcount=1](http://ubuntuforums.org/showpost.php?p=11020435&postcount=1)

---

### Post by canhoto on 2011-11-06
> **giguere56@gmail.com said:**
> **keyboard problem**             
                                                                here goes:

I cannot get the arrow keys to work... all of them: left, right, up and down.

I am running ubuntu 10.04 on a powerbook G4 model number A1095:
[http://www.everymac.com/systems/appl...g4_1.5_15.html]("http://www.everymac.com/systems/apple/powerbook_g4/stats/powerbook_g4_1.5_15.html")

When i look at the keyboard preference it says USA Macintosh. Further  down that keyboard preference window it says that my keyboard model is:

Generic 105 key ( intl ) PC.

Also the only way I can get the touchpad working is to go to the Terminal everytime I start the laptop and type:

sudo trackpad tap 

and 

sudo trackpad drag.

Is there a way to make this permanent?

Thanks
I'm not using a Powerbook, so I can't help you with the trackpad problem.

But I'm using a PowerMac and I had some problems with the keyboard at the beginning.

So, for the arrow keys problem, I suggest that you try to change the preferences in several ways. Frst, by changing the keyboard model preference and see what happens. If you can't (or if it's diimed), change the general layout: maybe USA Macintosh, although the obvious choice, isn't the wright one. Try severeal combinations between keyboard layout and keyborad model, even if they seem stupid. Yoy'll probably find the right one. Don't forget you have a preview window within the keyboard preferences to test your choices before applying them.

Now I'm using a Logitech keyboard (my Apple one was having some keys stuck) and everything seems to be ok. But, of course, on a laptop like your Powerbook it's not so practical to have an external keyborad.

---

