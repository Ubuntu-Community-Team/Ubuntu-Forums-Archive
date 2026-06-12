---
title: "A couple of theme questions...."
date: 2007-11-28
forum: Art &amp; Design
---

### Post by mikebeecham on 2007-11-28
Hi guys...

As a new Ubuntu user, there are a couple of probable newbie questions....sit tight:

1) Is there any way to drop the opacity of the panels?  I have seen a couple of GTK2 themes in Deviantart where the panel was a touch opaque...is this relevant to the theme, or can this be manually changed somewhere?

2) Is there any way to change the Ubuntu logo to the gnome foot?  I followed a tutorial somewhere else that mentioned using a Tango folder, but I do not have a tango folder....if anyone is able to break this down for me in easy to follow steps then that would be great!

Finally, can someone please explain to me the differences in all these theme elements....we have metacity, compiz themes, eXperience, etc.  I dont know what I need to install or activate in order to get themes to work?


HELP!!!

---

### Post by aashay on 2007-11-28
right click an empty area on the panel -> properties -> background -> solid color. Move the slider to adjust opacity
Regarding changing the ubuntu logo: there is a file distributor-logo.png somewhere. Replace it with whatever png you want.

---

### Post by mikebeecham on 2007-11-28
aashay...

No doubt I could find the foot to replace it with...but are you, therefore, saying that I should only be able to find one distributor-logo.png file and THAT is the one I should be replacing?

---

### Post by Hairy_Palms on 2007-11-28
some themes have there own distributor-lgoo.png, usually stored under scaleable/apps/distributor-logo.png.

---

### Post by mikebeecham on 2007-11-28
hairy...so I should just find the icon package that I am using at the time (/usr/share/icons/xxx) and replace the png file there?

---

### Post by Hairy_Palms on 2007-11-28
aye, alternatively you can set it via a gconf key, 
run gconf-editor and browse to
/apps/panel/default_setup/objects/menu_bar
and tick use_custom_icon
and enter the location of the icon you want to use.

---

### Post by smartboyathome on 2007-11-28
Metacity themes are the window border themes for GNOME. Compiz themes are themes that use the Emerald Window Decorator (you have to install it separately). The advantages of Emerald are that they are able to use compositing effects, while metacity themes can not. By default Ubuntu uses Metacity with Compiz with gtk-window-decorator (since Metacity and Compiz are both Window Managers, they can't be run at the same time, and thus a window decorator is used).

GTK thems are the themes that change how the inside of your window looks, and sometimes come with a metacity theme. You can find all your themes on gnome-look.org.

eXperience is just a partitcular theme to make your computer look like XP.

---

### Post by mikebeecham on 2007-11-29
On that basis, I installed Emerald, and can now see it in my Syetem > Preferences.  I can even open it up....but nothing I do changes the look of the windows...

What am I doing wrong here?

---

### Post by smartboyathome on 2007-11-29
You need to type emerald --replace while compiz is running.

---

### Post by mikebeecham on 2007-11-29
> **Hairy_Palms said:**
> aye, alternatively you can set it via a gconf key, 
run gconf-editor and browse to
/apps/panel/default_setup/objects/menu_bar
and tick use_custom_icon
and enter the location of the icon you want to use.

I tried that, assuming that I right click on "custom_icons" and create a new key.  From there though I am lost mate.

---

### Post by smartboyathome on 2007-11-29
There should be a section called custom_icon, put the path to your icon there.

---

### Post by mikebeecham on 2007-12-01
I did try that....there is a space to the right of custom_icon, where I placed the path to the icon. 

I then rebooted X, but nothing had changed?

---

### Post by Hairy_Palms on 2007-12-01
> aye, alternatively you can set it via a gconf key,
run gconf-editor and browse to
/apps/panel/default_setup/objects/menu_bar
**and tick use_custom_icon**
and enter the location of the icon you want to use.

did you tick use_custom_icon?
also theres no need to create a new key, if you did then youve done something wrong.

---

### Post by mikebeecham on 2007-12-05
Hi Hairy...

I did tick the checkbox and put the complete path (inc filename) in the appropriate area....

1) Should the icon (which is in png format) be in a particular place?

2) Should it be png, or another format?


Thanks

---

### Post by smartboyathome on 2007-12-05
I don't think it should be in any particular place, and it doesn't have to be in any particular format.

---

### Post by mikebeecham on 2007-12-06
then I dont know why it wont change...I've followed all the steps and no result.

---

### Post by smartboyathome on 2007-12-06
I don't know either... :S

---

