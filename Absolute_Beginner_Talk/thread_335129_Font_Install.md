---
title: "Font Install"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by TBayCrusher on 2007-01-09
After Using Windoze's NoBrainer Font Install, I Figured I'd Have No Trouble Putting A .TTF Font File Into Ubuntu. Geesh Was I Wrong. 
Have Browsed The Forums Here For Several Hours & From What I Can Figure, Installing Fonts Is One Of The Least Intuitive Things One Can Try To Do?!? Odd. 
I Did The System/Help Thing, That Didn't Really Tell Me What I Needed To Know At All. Tried About 12 Different Methods To Get The Font In The  Usr/Share/Fonts/TrueTypeFonts Folder, But To No Avail. It Just Will Not Go. 
I Need This School-Dashed-Interlined Font Installed For My Son's School Work. 
I Sure Hope I Can Sort It. ](*,)

---

### Post by firenurse4 on 2007-01-09
One option would be to create a hidden fonts folder inside your home directory.  While in you home folder in nautilus right click and create a folder and name in [COLOR="Blue"]**.fonts**[/COLOR]

Make sure there the period before fonts is there.  Pressing <CTRL> and H at the same time in nautilus will allow you to see the hidden folder.  Then paste the required font into that folder.

Remember that only that user will have use of that font.

Hope that helps.

---

### Post by TBayCrusher on 2007-01-11
Yes, This Seems To Have Sorted Things. 
I Would Not Have Thought Of This. :-k 
Thank You Kindly Firenurse. Much Appreciated

---

### Post by Jagermaster on 2007-01-12
> **firenurse4 said:**
> One option would be to create a hidden fonts folder inside your home directory.  While in you home folder in nautilus right click and create a folder and name in [COLOR="Blue"]**.fonts**[/COLOR]

Make sure there the period before fonts is there.  Pressing <CTRL> and H at the same time in nautilus will allow you to see the hidden folder.  Then paste the required font into that folder.

Remember that only that user will have use of that font.

Hope that helps.

WOW! That is a neat trick!
I had no idea that you could see so much by <CTRL> H in your home folder!
They should tell us things like this up front ](*,) I took a very long approach to adding fonts last time...lol

Thanks for that tip.

---

### Post by Delkster on 2007-01-12
> **firenurse4 said:**
> One option would be to create a hidden fonts folder inside your home directory.  While in you home folder in nautilus right click and create a folder and name in [COLOR="Blue"]**.fonts**[/COLOR]

Make sure there the period before fonts is there.  Pressing <CTRL> and H at the same time in nautilus will allow you to see the hidden folder.  Then paste the required font into that folder.

Another, perhaps a slightly more intuitive way of doing it would be to open **System > Preferences > Font**, then **Details**, and finally **Go to font folder**. You should then be able to drag and drop the font into that folder. It doesn't seem to appear in the folder (that's a slight bug) but it should be usable after that. What actually happens when you do this is that the font is placed in the .fonts folder so the result is the same.

You may need to restart your application in order to have the new font usable. Logging out and back in should be a safe bet.

---

### Post by Delkster on 2007-01-12
> **Jagermaster said:**
> I had no idea that you could see so much by <CTRL> H in your home folder!

If you take a look at the **View** menu in the file manager, you'll see an option called "Show Hidden Files". The shortcut key of Ctrl+H is also displayed. ;-)

---

### Post by carla on 2007-01-12
Don't forget:

After installing any new fonts, refresh your font cache:

```
sudo fc-cache -f -v
```

---

