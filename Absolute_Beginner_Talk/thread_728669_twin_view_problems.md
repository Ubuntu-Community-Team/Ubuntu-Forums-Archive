---
title: "twin view problems?"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by jeffinhedon on 2008-03-19
I have been trying for ages to get Twin View to work here
My card is GeForce FX 5200
I got round to making changes /additions to the xorg.conf file after trying to change thing using the menus
I have done something wrong however
After the last change I re-booted
And the thing starts to boot then just turns the screen off and hangs
There must be a way of reversing these changes
I can boot up to the recovery stage 
But I dont know what to do next 
I guess there is a control sequence  I can activate to replace the xorg .conf file that I have obviously corrupted.
BUT how do I do that ?
Please help if you can 
Its driving me  round the bend
As an absolute Newbie its a hard way to learn!!!!:(
Any advice will be very much appreciated

---

### Post by ad_267 on 2008-03-19
You can run "sudo dpkg-reconfigure -phigh xserver-xorg" to revert your xorg.conf file back to the default settings.

How are you trying to set up twin view?

I enabled the restricted driver then ran "sudo nvidia-settings" and enabled twin view from there and everything worked fine.

---

### Post by jeffinhedon on 2008-03-19
Well that was remarkable!!!
I run the reconfigure command as you suggested.
I then got a serires of screen asking me to select various options !!!
I guess thats a manual configure method?
I then rebooted 
Activated the "restricted drivers"
I then found that I could ajdust the varios screen settings by using the 
"Screen and graphics" window in the Administration menu
Now the Situation is
Twin screens no working
the task bars both top and bottom are only on the main screen and the second screen is just clear but if I want to open an application I can now use both screens
So thats about as good as it can get ....Thanks a lot :)
I had previously tried to install a nvidia driver using apt...but I really didnt know what I was doing
It might be a good thing to flag this thread as a good example of how to tackle this particular prob
Once again Many many thanks

---

### Post by ad_267 on 2008-03-20
Did you try using "sudo nvidia-settings"?

I've found this works a lot better than the "screens and graphics" settings.

Also if you use the -phigh option with dpkg-reconfigure it should select all the default settings for you so you don't need to choose any options.

---

### Post by jeffinhedon on 2008-03-20
Yes I used the nvidia setting option
and it works a treat!!!!
BTW when I used the command to reconfigure as you suggested 
the phigh part didnt work
but none the less I got it back working 
thanks to your advice 
Many thanks

---

### Post by THe.Conundrum on 2008-03-22
i also am having a problem getting twinview to work i've tried what you guys say to do and a few other things and when i type in nvidia-settings it pop up but it only has a single option tree which allows me to set 

nvidia-settings configuration
[INDENT]Enable ToolTips
Display Status Bar
Slider Text Entries
Include X Display names in the config file
Show "Really Quit?" Dialog[/INDENT]

---

