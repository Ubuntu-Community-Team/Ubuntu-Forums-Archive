---
title: "What kind of image does an icon have to be?"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by CheshireMac on 2006-11-26
I'm trying to customize Dapper to my liking, but I can seem to find out how to change icons to my own versions . . .only what's given in the icons folder. I tried to move some the way gnome-look told me, but I must be missing a step (or they are). ~LOL~ A little help?

---

### Post by WiseElben on 2006-11-26
Icons can be PNG, JPG, or GIF. I'm not sure about SVG, and I'm pretty sure ICOs are not supported, as it is a Windows format type.

---

### Post by Cardmaster91 on 2006-11-26
rlly? jpgs can? it doesnt show jpeg images when im selecting an icon

not that its much of a problem w/ gimp. it can save them as anything

---

### Post by CheshireMac on 2006-11-26
Okay . . .so something's definataely out of place . . .how, in terminal, can I get an image to work as an icon? I'm trying to change my Firefox and Thunderbird icons first ...mostly because they look lame with the default on Dapper. ~LOL~ Thanks for the help.

---

### Post by Cardmaster91 on 2006-11-26
idk how to do it from terminal, but if u right click on the icon and click on properties, just click the icon and navigate to ur pic

---

### Post by CheshireMac on 2006-11-26
I've tried that, but the image doesn't show up whenever I naviagate to it's location to select it as an icon . . .weird? Or am I missing something?

---

### Post by Cardmaster91 on 2006-11-26
check wat kind of file it is, try making it a ping

---

### Post by CheshireMac on 2006-11-26
It is a png . . .and I've tried converting it to a couple other formats in Gimp . . .it doesn't seem to be working. This is fairly frustrating for a simple icon switch. ~LOL~ I should just be able to paste the icon to the icons folder, shouldn't I?

---

### Post by Cardmaster91 on 2006-11-26
could u give me a screenshot of the "empty" folder that u navigated to (try seperating the windows so i can see em all), b/c i havent rlly used dapper in a while

---

### Post by CheshireMac on 2006-11-26
Here's the two folders . . .I can't drag it, copy it, or cut it over to the proper folder. Is there a way to get around that permission, or am I going about it the wrong way?

---

### Post by user1397 on 2006-11-26
as far as i know, PNG's and GIF's are used for gnome icons...
the two primary directories for icons are /usr/share/icons and /usr/share/pixmaps

to move an icon you created, and that's saved on your desktop, in a terminal you would type:
```
cd ~/Desktop
sudo mv ICONNAME /usr/share/icons
(enter your password here)
```
if it doesn't show up, you must refresh your panels ```
killall gnome-panel
```
if even that doesn't work, try logging out and back in, or even restarting (extremely rare to have to do this)

---

### Post by Cardmaster91 on 2006-11-26
i think u may be going about it the wrong way. first of all, i noticed ur icon had a .th.png. i first recommend trying to remove that .th

and i dont think u need to be in the icons folder, just right click on the icon u wish to change, then navigate to the folder ur icon is in (/mac/thunderbirdicons)


p.s. 
i noticed that u changed ur background, could u pls tell me the driectory the backgrounds are in?

---

### Post by CheshireMac on 2006-11-26
Error while copying to "/usr/share/...rbird/icons".
You do not have permissions to write to this folder.

This is the error I'm getting, and I even converted the image to XPM just to be safe . . .this is odd . . .I tried moving it through Terminal, but it told me there was no such directory as /usr/share/mozilla-thunderbird/icons. ~LOL~ I know I'm doing something stupid. . .sorry for the noob ignorance.

---

### Post by CheshireMac on 2006-11-26
> **Cardmaster91 said:**
> i think u may be going about it the wrong way. first of all, i noticed ur icon had a .th.png. i first recommend trying to remove that .th

and i dont think u need to be in the icons folder, just right click on the icon u wish to change, then navigate to the folder ur icon is in (/mac/thunderbirdicons)


p.s. 
i noticed that u changed ur background, could u pls tell me the driectory the backgrounds are in?
I got this background simply by right clicking the image in Firefox. ~LOL~ I don't know how to permanently add the image to the dir.

---

### Post by user1397 on 2006-11-27
are you using the "sudo" command in the terminal before moving them to the desired folder?  or else, it will not grant u permissions.  just follow my advice at the top, and see how it works out.

---

### Post by CheshireMac on 2006-11-27
That's what I did. Sudo, and got the password correct. It just won't let me do it . . .it tells me in the browser that I don't have permission, and in the terminal, the dir. doesn't exist.

---

### Post by Cardmaster91 on 2006-11-27
> **CheshireMac said:**
> I got this background simply by right clicking the image in Firefox. ~LOL~ I don't know how to permanently add the image to the dir.

o :(

---

### Post by user1397 on 2006-11-27
you're not supposed to just right-click and save as background, right-click and choose save-as, and save in desktop.  and you're not supposed to put it into the mozilla-thunderbird dir, put it in the dir that i said, /usr/share/icons (with the sudo command)

then you can right click on your applications menu, select edit menus, and then navigate to the thunderbird entry, and click on the icon for it, and browse to /usr/share/icons and you'll find it there.

---

### Post by IYY on 2006-11-27
I'm not sure exactly what you are asking, possibly because there are so many confusing replies, but if you want to set the icon of a specific application, here's how it's done:

Right click on the application/directory/shortcut you wish to set the icon on. Select `Properties'. Open your file browser in the regular way, find the PNG image you wish to use as the icon, and drag it into the box beside the name of the program (there may already be an icon in it). It should work!

---

### Post by CheshireMac on 2006-11-27
> **IYY said:**
> I'm not sure exactly what you are asking, possibly because there are so many confusing replies, but if you want to set the icon of a specific application, here's how it's done:

Right click on the application/directory/shortcut you wish to set the icon on. Select `Properties'. Open your file browser in the regular way, find the PNG image you wish to use as the icon, and drag it into the box beside the name of the program (there may already be an icon in it). It should work!

Ivy, you're a genious! ~LOL~ The simplest of solutions, right in front of me, and it's the only one I didn't try. ~LOL~ Thank you.

---

### Post by Ben Sprinkle on 2006-11-27
IVY is correct. Most always use .png as it's probably the most compressed with retaining the best quality. It's what almost everyone is using nowadays anyway.

---

