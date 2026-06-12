---
title: "Steam + Counter Strike + WINE Problem help!!"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by 187eR on 2007-07-16
ive been using linux ubuntu for about 5 days. i got pretty familiar with it . my problem is that then i run steam using WINE there is no text in the steam program..now i have already check the forums and found a guy with the same problem....but he had not installed the tahoma font, i have done that and stiil, it dosent work, any suggestions ppl 

thanks in advance!


file:///home/mimik187er/Desktop/Screenshot.png

---

### Post by Fitzy_oz on 2007-07-16
> **187eR said:**
> ive been using linux ubuntu for about 5 days. i got pretty familiar with it . my problem is that then i run steam using WINE there is no text in the steam program..now i have already check the forums and found a guy with the same problem....but he had not installed the tahoma font, i have done that and stiil, it dosent work, any suggestions ppl 

thanks in advance!


file:///home/mimik187er/Desktop/Screenshot.png

Where did you install the Tahoma font to?
I had a windows installation handy for mine and simply copied the entire windows/fonts directory from the windows computer to ~/.wine/drive_c/windows/fonts.  This resolved the issue.  If windows is not available try downloading Lucida console, Lucida sans and MS Sans Serif also.

---

### Post by 187eR on 2007-07-17
thanks for your reply, i tried what u suggested  but it didint work eather. i coped the fonts from my winxp to the directory, but no luck. funny thing is that its fully functional games run well i get a steady 100 fps in counter strike . but the only thing is that the text wont show up so i have to idea what server i am joining,basically its VERY hard to navigate. i think that its just some kind of bug or something cuz i did everthing right and there are a couple pll with the same problem. i also found this in the wed

	
Missing fonts workaround
by Krzysztof Lichota on Saturday October 29th 2005, 19:00
When running from standard install no text is displayed.
There was an advice to install tahoma.ttf font but it is not freely available. So I worked around it in the following way:
1. Open .wine/system.reg in text editor.
2. Find key [Software\\Microsoft\\Windows NT\\CurrentVersion\\FontSubstitutes]
3. Add subkey:
"Tahoma"="Times New Roman"

also this wed site [http://www.vikrammohan.com/blog/2006/12/06/solution-for-when-steam-shows-no-text-on-wine/](http://www.vikrammohan.com/blog/2006/12/06/solution-for-when-steam-shows-no-text-on-wine/)

but i don't understand what exactly to do, like i said am new to linux .. if someone with more experience with linux can help me, ill be very appreciative. :)

---

### Post by Fitzy_oz on 2007-07-17
> **187eR said:**
> thanks for your reply, i tried what u suggested  but it didint work eather. i coped the fonts from my winxp to the directory, but no luck. funny thing is that its fully functional games run well i get a steady 100 fps in counter strike . but the only thing is that the text wont show up so i have to idea what server i am joining,basically its VERY hard to navigate. i think that its just some kind of bug or something cuz i did everthing right and there are a couple pll with the same problem. i also found this in the wed

	
Missing fonts workaround
by Krzysztof Lichota on Saturday October 29th 2005, 19:00
When running from standard install no text is displayed.
There was an advice to install tahoma.ttf font but it is not freely available. So I worked around it in the following way:
1. Open .wine/system.reg in text editor.
2. Find key [Software\\Microsoft\\Windows NT\\CurrentVersion\\FontSubstitutes]
3. Add subkey:
"Tahoma"="Times New Roman"

also this wed site [http://www.vikrammohan.com/blog/2006/12/06/solution-for-when-steam-shows-no-text-on-wine/](http://www.vikrammohan.com/blog/2006/12/06/solution-for-when-steam-shows-no-text-on-wine/)

but i don't understand what exactly to do, like i said am new to linux .. if someone with more experience with linux can help me, ill be very appreciative. :)


I haven't seen that before, you're not running wine with sudo are you?  from the terminal try running wineprefixcreate to update the registry settings....

---

