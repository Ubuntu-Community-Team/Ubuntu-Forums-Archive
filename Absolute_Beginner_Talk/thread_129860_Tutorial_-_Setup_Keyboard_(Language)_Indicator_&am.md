---
title: "Tutorial - Setup Keyboard (Language) Indicator &amp; Install Foreign (Language) Fonts"
date: 2006-02-14
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-02-14
**Tutorial:**

**How to Setup Keyboard (Language) Indicator & Install Foreign (Language) Fonts in Ubuntu: **


1. On an Empty area of the Menu, right-click & select "Add to Panel...".

2. On the "Add to Panel" window that shows up, scroll down with the scroll bar on 
    the right & under the Utilities section, select "Keyboard Indicator".

3. Click on the button named "Add" & a Keyboard Indicator Icon should appear in 
    the middle of your Menu Toolbar (e.g. in My Computer, a "USA" keyboard 
    indicator showed up – in your PC, a diff Language could show, depending on 
    what Keyboard you selected when you installed Ubuntu)

4. Right-click on your "Keyboard Indicator" & select "Open Keyboard Preferences".

5. On the "Keyboard Preferences" window that shows up, select the Tab named 
    "Layouts".

6. Under the "Keyboard model", you should see the "Generic 104-key PC".

7. Under the "Selected layouts" section, YOUR installed Keyboard Layout should 
    show (e.g. as I said before in my case it is "U.S. English"). Click on the button 
    named "Add", to install a Second Keyboard Layout.

8. In my case, I selected "Greece".
    Note:
    If you select to install a Greek Keyboard Layout, do NOT expand the "Greece" 
    folder (you would get: Eliminate dead keys, Extended & Polytonic). Just select 
    "Greece" & click on the button named "OK". For other Keyboard Languages, you 
    are on your own to experiment & find out which selection works for you.

9. Now you should be able to see your installed "Selected layouts".
    Note:
    To install more Keyboard Layouts, follow steps 7-9.
    To remove a Keyboard Layout, first select it & click on the button named 
    "Remove".

10. On the "Keyboard Preferences" window, select the Tab named: "Layout 
      Options"

11. Look for the option named: "Group Shift/Lock behavior" & expand it, to see its 
      options.

12. The following two options should be selected:

	a. "Both Alt keys together change group."	(this should already be 
                                                                                  checked – leave it checked)
	b. "Alt + Shift changes group."		                (check this too)
	    Note:
            The combination "Alt+Shift", should change your Keyboard (Input) 
            Indicator, the same way it works in the Windows environment.  

13. Click on the button named "Close" & test your "Alt+Shift" or "Alt+Alt" 
      combination to see whether the  Keyboard (Input) Indicator changes on your 
      Menu Toolbar.

14. To Test whether your Ubuntu's Editor (mine is "gedit"), works with ALL your 
      installed Keyboard Layouts, select "Alt+F2". "Alt+F2" is the shortcut (way) to 
      launch the similar to Windows "Start\Run" window.

15. Inside the input box, type your favorite Editor's name (mine is "gedit").

16. Inside the Editor, try to type something in your English Keyboard & then try to 
      switch to your Greek Keyboard (or the one YOU installed), by pressing 
      "Alt+Shift". Again, try to type something in your (newly installed) Greek 
      Keyboard (or the one YOU installed) & voila!!! your Country's Keyboard is 
      setup & works Great!!!


Important Notes:

1. The (New) Keyboards you have ADDED, are installed ONLY for the User you are 
    currently Logged In as. If your Computer is used by MORE than one User, each 
    User MUST separately ADD / INSTALL their own preferred Keyboards. And that 
    includes the "root" user too!!!

2. The The (New) Keyboards you have ADDED, can ONLY be used to type Keyboard 
    (Language) Characters in applications / programs embedded to your Operating 
    System. The fact that you have installed them, does NOT mean that you can 
    USE them in separate applications / programs ALSO (such as the Open Office's 
    Writer – e.g. the equivalent to Microsoft Word).

3. In order to be able to type in your Open Office Writer with YOUR Language's 
    Fonts, you MUST install the appropriate Fonts for your Language.
    For Example: 
    To be able to type in Open Office Writer (e.g. the equivalent to Microsoft Word) in 
    Greek you MUST go into a Windows PC and  copy the ".ttf" (True Type Fonts) that 
    are used more often in typing Greek. In our case, copy: the "Times New 
    Roman.ttf", the "Arial.ttf" & the "Sans Seriff.ttf". 
    Alternatively, you could also search for these Fonts in the Internet.
    Note:
    You can NOT install ".fon" type Fonts in Ubuntu. ONLY ".ttf" (True Type Fonts).
    
    For more information on installing Fonts, visit the following link:

	[http://linuxhelp.blogspot.com/2005/12/adding-windows-fonts-in-linux.html](http://linuxhelp.blogspot.com/2005/12/adding-windows-fonts-in-linux.html)

    Note:
    Keep in mind that Open Office does NOT use the SAME Fonts installed / used by 
    the Operating System (e.g. Ubuntu). However, the Fonts installed are 
    independent from the User. Every User can access / use ANY installed Font.
    And there is NO Greek Font available for the "root" User.
    To make things more clear, just visit the link specified above.

Have Fun!!!

---

### Post by bountonw on 2006-02-14
This thread on setting up multi-language support is also good.

[http://www.ubuntuforums.org/showthread.php?t=102760](http://www.ubuntuforums.org/showthread.php?t=102760)

---

### Post by midra on 2006-04-23
Hi there, I did this, but the indicator does not change. I just still get my default language, but I cannot get the language I added, although it is in the layouts list.](*,)

---

### Post by midra on 2006-04-23
Okay, if I click the indicator with my mouse it changes so it works, but I still cannot get it to change with my keyboard ALT + ALT nor ALT + SHIFT although they are enabled. Uh well, but as said, the mouse is working and that is as good as needed for me.

---

### Post by Costas on 2006-04-23
It really helped me installing the greek keyboard on my Ubuntu..thanxs a lot for the advices dvarsam! Keep up the fantastic work!

---

### Post by Costas on 2006-04-23
forgot to mention: it's awesome that such forums exist...especially for guys like me who got into Ubuntu (or linux in general) something like 3 weeks ago....and intend NEVER to use MS again...i was forced to get involved with linux, since i had to use a program that needed Lapack and was working in linux only....but thank God that i had to discovet linux!

thanx guys!

---

### Post by xinelo on 2006-09-30
Thanks for the tutorial, very clear. 

It explains what I had already done myself but, unfortunately, it doesn't work for me, neither with mouse clicking nor with keyboard shortcut. 

Any suggestions? 

I'm using Ubuntu Dapper on a Dell Inspiron 8500 and I'd like to be able to type in Arabic. 

Thanks a lot!
Cheers, xinelo

---

### Post by dgbraun on 2006-11-07
I have the opposite problem. It seems that when flash is in use on some websites or in trying to install programs under wine, the font is some type of greek/russian/cyrillic. How can I reset this to latin/english?
Thanks

---

### Post by mormonchess on 2006-11-28
Why only a maximum of 4 layouts?? In Windows, you can have all the layouts you want.  Most irritating.

Is there any work around?

---

### Post by simosx on 2006-12-19
> **mormonchess said:**
> Why only a maximum of 4 layouts?? In Windows, you can have all the layouts you want.  Most irritating.

Is there any work around?

As far as I know there is no workaround. I hope it is sorted out soon. You can use a different system though to switch layouts such as SCIM which allows for more.

---

### Post by simosx on 2006-12-19
> **dvarsam said:**
> **Tutorial:**

**How to Setup Keyboard (Language) Indicator & Install Foreign (Language) Fonts in Ubuntu: **

...

8. In my case, I selected "Greece".
    Note:
    If you select to install a Greek Keyboard Layout, do NOT expand the "Greece" 
    folder (you would get: Eliminate dead keys, Extended & Polytonic). Just select 
    "Greece" & click on the button named "OK". For other Keyboard Languages, you 
    are on your own to experiment & find out which selection works for you.



I think it is better to expand the Greece "folder" and pick "Extended". 
With "Extended" you will be able to type the Euro sign and also the Greek brackets (the ones that look like << and >>.

See 
[http://webcvs.freedesktop.org/xkeyboard-config/xkeyboard-config/symbols/gr?view=markup](http://webcvs.freedesktop.org/xkeyboard-config/xkeyboard-config/symbols/gr?view=markup)
for the details between Extended, Polytonic, etc. If you do not expand the Greece "folder", you implicitly choose the first layout in the list.

> **dvarsam said:**
> **Tutorial:**

...

12. The following two options should be selected:

	a. "Both Alt keys together change group."	(this should already be 
                                                                                  checked – leave it checked)
	b. "Alt + Shift changes group."		                (check this too)
	    Note:
            The combination "Alt+Shift", should change your Keyboard (Input) 
            Indicator, the same way it works in the Windows environment.  


Generally I prefer to have only Alt-Shift active. You can disable the Alt-Alt combination.
Now, if you have three or more layout selected, this may cause in some cases problems when you try to switch between layouts with Alt-Shift; you may notice that the keys "get stuck".

> **dvarsam said:**
> **Tutorial:**

...

14. To Test whether your Ubuntu's Editor (mine is "gedit"), works with ALL your 
      installed Keyboard Layouts, select "Alt+F2". "Alt+F2" is the shortcut (way) to 
      launch the similar to Windows "Start\Run" window.

15. Inside the input box, type your favorite Editor's name (mine is "gedit").



You can get "gedit" from Applications/Accessories/Text Editor as well.

> **dvarsam said:**
> **Tutorial:**

...

2. The The (New) Keyboards you have ADDED, can ONLY be used to type Keyboard 
    (Language) Characters in applications / programs embedded to your Operating 
    System. The fact that you have installed them, does NOT mean that you can 
    USE them in separate applications / programs ALSO (such as the Open Office's 
    Writer – e.g. the equivalent to Microsoft Word).

3. In order to be able to type in your Open Office Writer with YOUR Language's 
    Fonts, you MUST install the appropriate Fonts for your Language.
    For Example: 
    To be able to type in Open Office Writer (e.g. the equivalent to Microsoft Word) in 
    Greek you MUST go into a Windows PC and  copy the ".ttf" (True Type Fonts) that 
    are used more often in typing Greek. In our case, copy: the "Times New 
    Roman.ttf", the "Arial.ttf" & the "Sans Seriff.ttf". 
    Alternatively, you could also search for these Fonts in the Internet.
    Note:
    You can NOT install ".fon" type Fonts in Ubuntu. ONLY ".ttf" (True Type Fonts).
    
    For more information on installing Fonts, visit the following link:

	[http://linuxhelp.blogspot.com/2005/12/adding-windows-fonts-in-linux.html](http://linuxhelp.blogspot.com/2005/12/adding-windows-fonts-in-linux.html)

    Note:
    Keep in mind that Open Office does NOT use the SAME Fonts installed / used by 
    the Operating System (e.g. Ubuntu). However, the Fonts installed are 
    independent from the User. Every User can access / use ANY installed Font.
    And there is NO Greek Font available for the "root" User.
    To make things more clear, just visit the link specified above.



Since Ubuntu 6.06 (ok, you posted this article before that version of Ubuntu), the distribution comes with Greek font support by default, using the DejaVu fonts that support modern and ancient greek.
These fonts are installed properly, therefore they are available to any user without any additional configurations.

There is an Ubuntu-Gr mailing list, at
[https://lists.ubuntu.com/mailman/listinfo/ubuntu-gr](https://lists.ubuntu.com/mailman/listinfo/ubuntu-gr)

---

### Post by PyrSos_ on 2007-06-06
Thanks a lot for your precious help! 
Works fine for me!

---

