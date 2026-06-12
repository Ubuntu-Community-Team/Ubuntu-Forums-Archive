---
title: "Help with skim on Kubuntu 6.06"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by pizzat104 on 2006-07-04
I am trying to get skim to work on Kubuntu 6.06. I've installed it through Adept and have also enabled Chinese through the Language Support via the Settings menu. The skim icon appears in the task bar, but when I right click, the input method list is empty.

I'm a beginner so any help would be greatly appreciated!

---

### Post by catlett on 2006-07-04
I do not run kubuntu so I don't have any knowledge about this issue. But I thought I would point out the obvious just in case it was missed.
Did you reboot after installing?
Did you enter "skim on kubuntu" in the search box on the upper right and see what results you got?

Sorry not to have a real answer. Just thought I would throw a couple of things out and bump your post up at the same time.

---

### Post by pizzat104 on 2006-07-04
I tried rebooting and before posting I did a little search. I found some posts with similar problems, namely

[http://www.ubuntuforums.org/showthread.php?t=171147&highlight=skim+chinese](http://www.ubuntuforums.org/showthread.php?t=171147&highlight=skim+chinese))
[http://ubuntuforums.org/showthread.php?t=167341&highlight=skim](http://ubuntuforums.org/showthread.php?t=167341&highlight=skim)

a) How do you edit your environment file - I can't save changes
b) I tried running the command "QT_IM_MODULE=scim kate" in the Konsole but that didn't work either.

Again, any help would be appreciated.

---

### Post by catlett on 2006-07-04
According to your second posted link, you can edit /etc/environment. Open the konsole and enter ```
sudo kate /etc/environment
``` When the document comes up, enter this text ```
QT_IM_MODULE=scim
``` reboot and that should be it. 
Again this is what I get out of the second link.

P.S. It also mentioned that if you were going to use gnome or gnome apps, enter this in the same document ```
GTK_IM_MODULE=scim
``` Good luck. Sorry I don't have a definitive answer.

---

### Post by pizzat104 on 2006-07-05
Thanks for your response. I added the line to the environment file and rebooted, but still the same result. I'm thinking maybe the second link may not be the answer. In my skim configuration, I have the IM engines enabled, but I still am unable to choose a language when I open Kate. Any other ideas?

Thanks in advance.

---

### Post by catlett on 2006-07-05
The first link had a response where the poster said adding to /etc/environment worked but he aded that he added Chinese to Language supot. Have you done that at?
You get there by going to the top panel and choosing System<Administration<Language Support.

I have to go to work buit wqhen I get back if you still have issues I'll search for an answer.

---

### Post by pizzat104 on 2006-07-05
I actually did install the language support before changing the /etc/environment file. I should have done everything that was mentioned in that post, but still no language input...

---

### Post by catlett on 2006-07-05
[https://help.ubuntu.com/community/SCIM/Kubuntu?action=show](https://help.ubuntu.com/community/SCIM/Kubuntu?action=show)  Have you seen this? Have you taken all these steps already? There are no bugs reported for skim so it should install and work.

This is from the dapper guide. I don't know if it ubuntu specific or not. The guide just says dapper but it is mostly ubuntu specific but I thought I would post it as well [http://doc.gwos.org/index.php/DapperGuide#How_to_install_Chinese_Input_Method_.28SCIM.29](http://doc.gwos.org/index.php/DapperGuide#How_to_install_Chinese_Input_Method_.28SCIM.29)

---

### Post by pizzat104 on 2006-07-06
Thanks so much for your responses. I'm gonna give it a try again tomorrow following those step by step instructions. I agree that it's gotta be me doing something wrong. 

I'll post the results after I try it again.

Thanks!

---

### Post by Hiroshima on 2006-07-07
I had the same problem with Japanese, so I searched and found this thread.  

This link [https://help.ubuntu.com/community/SCIM/Kubuntu?action=show](https://help.ubuntu.com/community/SCIM/Kubuntu?action=show) posted by catlett looks perfect.  Should help you with Chinese... my problem is I want Japanese, and in the example is says in a terminal enter: 

cp /etc/X11/xinit/xinput.d/scim-pinyin ~/.xinput.d/default

But I don't want pinyin, I want Japanese.  Anybody know what file name I should use here?

Thanks,

Hiroshima

Good luck Pizzat104

---

### Post by pizzat104 on 2006-07-09
Hiroshima, were you able to get it to work?

I followed the instructions step by step. I removed everything (skim, scim, language support). Then I installed skim through adept. I added the language support for chinese (does the order matter? I'm guessing not). I made the folder .xinput.d/default and then I copied the file through the Konsole. I don't know if there was a potential for a mess-up at that step. Then I restart, open Kate, open skim, and control+space and right clicking on the skim icon both do nothing.

I have no idea why this isn't working!

Also, just to see the results, I changed my default language to Chinese so that the KDE menu was also in Chinese. I was able to input in Chinese that way, but how do I get it to work so that I have an English desktop with the option to input Chinese?

Thanks again!

---

### Post by Hiroshima on 2006-07-14
> **pizzat104 said:**
> Hiroshima, were you able to get it to work?


Also, just to see the results, I changed my default language to Chinese so that the KDE menu was also in Chinese. I was able to input in Chinese that way, but how do I get it to work so that I have an English desktop with the option to input Chinese?

Thanks again!

Sorry to take so long getting back... I thought I'd replied once, but I must not have hit the propper post button.

On your loggin screen, are there any language options?  I had those in Ubuntu, but don't seem to in Kubuntu.  If you do, that would be an easy fix.  Just logout, look for language options, and then choose an English session and log back in.

Yes, I did get Japanese working.  It seems to be going ok.  Have you had any luck since you last posted?

Hiroshima

---

### Post by Rastareefer on 2006-07-21
Any chance you can post how to get Japanese working in Kubuntu?
By some fluke, I had Anthy working in every program in the KDE desktop last week but have no idea how this occured and after re installing kubuntu today am pulling my hair out.

I need to be able to input, Hiragana, Katakana, and of course do the Kanji henkan.

Thanks in advance

---

### Post by Hiroshima on 2006-07-22
> **Rastareefer said:**
> Any chance you can post how to get Japanese working in Kubuntu?
By some fluke, I had Anthy working in every program in the KDE desktop last week but have no idea how this occured and after re installing kubuntu today am pulling my hair out.

I need to be able to input, Hiragana, Katakana, and of course do the Kanji henkan.

Thanks in advance

When I got my system working with Japanese, I used the advice here (use either or both):
[http://ubuntuforums.org/showthread.php?t=189834](http://ubuntuforums.org/showthread.php?t=189834)
and here:
[https://help.ubuntu.com/community/SCIM/Kubuntu?action=show](https://help.ubuntu.com/community/SCIM/Kubuntu?action=show)
If you are looking at the second link, you will need the line:
sudo cp /etc/X11/xinit/xinput.d/ja_JP ~/.xinput.d/en_GB (your language code) instead of the similar looking line on the page.  I think I used "default" rather than "en_GB" because I was running the default language settings.

If you want to run Skype or Acrobat reader, I would suggest trying UIM (instructions on the fisrt link) rather than Skim, because while I cannot load either of those programs due to a conflict with skim.  I am thinking of switching to UIM to get skype to work.  I can live without acrobat, as you can use xpdf
[http://ubuntuforums.org/showthread.php?t=125407](http://ubuntuforums.org/showthread.php?t=125407)
just use the xpdf instructions.
Also, if you use firefox, you can use a plugin for an online dictionary to help you read japanese pages
[http://ubuntuforums.org/showthread.php?t=188589](http://ubuntuforums.org/showthread.php?t=188589)

I hope you get your Japanese imput going!

---

### Post by pizzat104 on 2006-07-22
Unfortunately I haven't been able to get Skim working since my last post... I've just been pretty busy and started trying to fix the problem again this afternoon. 

I used the instructions from this link: [https://help.ubuntu.com/community/SCIM/Kubuntu?action=show]("https://help.ubuntu.com/community/SCIM/Kubuntu?action=show").

However, nothing happens when I click on the Skim icon. When it says to type this in Konsole:

> sudo cp /etc/X11/xinit/xinput.d/ja_JP ~/.xinput.d/en_GB (your language code)

(where ja_JP would be replaced by pinyin-scim in my case, and en_GB by default or en_US, I presume)

are the language folders (ie. en_GB, default, etc) supposed to exist already? They did not for me and so I created those folders. Also, how do you know which is the appropriate language code?

Thanks in advance.

---

### Post by Hiroshima on 2006-07-23
> **pizzat104 said:**
> Unfortunately I haven't been able to get Skim working since my last post... I've just been pretty busy and started trying to fix the problem again this afternoon. 

I used the instructions from this link: [https://help.ubuntu.com/community/SCIM/Kubuntu?action=show]("https://help.ubuntu.com/community/SCIM/Kubuntu?action=show").

However, nothing happens when I click on the Skim icon. When it says to type this in Konsole:



(where ja_JP would be replaced by pinyin-scim in my case, and en_GB by default or en_US, I presume)

are the language folders (ie. en_GB, default, etc) supposed to exist already? They did not for me and so I created those folders. Also, how do you know which is the appropriate language code?

Thanks in advance.


Pizza, this is a little over my head too, but lets see what we can do.

To see what language folders already existed on my system, I copied ~/.xinput.d/en_GB opened up a konqueror window and pasted it (~/.xinput.d/en_GB) into the address bar.  Then I backspaced over en_GB and hit enter.  I saw the language files there.  I have both en_GB and en_CA there.  They are both files _not_ folders.  You can tell they are files because there isn't a "/" after the name.

Ok, so what to do?

Maybe the first step is to open a Konqueror window, and find out what files are there by going to ~/.xinput.d/

Since I didn't have a en_US file there, but there is US listed when I look under K Menu>System Settings>Regional & Accessibility> Country Region & Language ... never mind, I just played with the settings, I don't think the two are necessarily related.

Then when you do the 
[COLOR="DarkOrange"]cp /etc/X11/xinit/xinput.d/scim-pinyin ~/.xinput.d/default[/COLOR]
well, try first with default
and second try with whatever file you found above.  I'm pretty sure I used  default when I did it, because I didn't check what was already there first.

Give that a try and see how it goes.  Follow all the steps from start to finish, even if you've done them before.

Good luck, Hiroshima

---

### Post by pizzat104 on 2006-07-23
It works!

Thanks Hiroshima. The problem was I made the ~/.xinput.d/default folder as opposed to copying the appropriate file under the .xinput.d folder as the file named default. I did that the first time I tried installing when I didn't know anything, and didn't realize that was the issue until now.

Thanks very much for your help! I can finally input Chinese. Now, is there a way to get more fonts; I tried looking through Adept but didn't really know what to choose. It seems as if the inputted characters are kind of fuzzy. 

Thanks again!

---

### Post by Hiroshima on 2006-07-25
About the fonts: When I was using Ubuntu Breezy, the fonts looked bad as well. I upgraded to Dapper, and the fonts were still fuzzy.  Finally, I did a clean e install of Dapper, and everything looked pretty good.  I can't promise you would get the same results, as your system is different.

With adept, if you search for Chinese fonts, what do you get?
Have you searched the forums for "fuzzy Chinese fonts" ?
If you don't get anything, try searching for fuzzy Japanese fonts.  I know there are threads out there from when I was trying to get Breezy to look good.  Some suggest fiddling with your fonts files in a console, and others will suggest fiddling with Kmenu>System settings>Personal Appearance>fonts from there you can fiddle with anti-aliasing - I can't remember what settings were recommended.  Anyhow, have a search, and if nothing comes up, post again, and I'll see if I have better luck searching.

PS, I'm glad you got SKIM to go!

Hiroshima

---

### Post by Rastareefer on 2006-07-27
Wowww...a few more distros later trying to get Japanese UIM working and I am back to Kubuntu. Thanks for all the help and suggestions while I was away.
I just need to get Anthy working mainly for use with Thunderbird, even though I can not get the Japanese input working I have no trouble reading Japanese in firefox, the problem is writing it and I have to write some reports in a couple of weeks which causes me concern over the UIM problems.

I did get Anthy working a couple of weeks ago but unfortunately the system got trashed due to some problems with the screen saver fix with the KDE desktop bug. After this, I can not for the life of me remember where I read the simple fix for UIM that worked with Anthy & I am reading tons of posts here some of which do not seem to work for most people and other fixes that are not too easy to follow for a newbie.

I fail to understand why scim & anthy come with these Linux distros but don't work.

---

### Post by Rastareefer on 2006-07-28
Found this somewhere deep in the anals of the Ubuntu forum which works in KDE on Kubuntu and is a no brainer to the extent that even I could manage it.

----------------------------------------------------------------------------
 * sudo apt-get install im-switch uim uim-anthy
   * im-switch -s uim_anthy
   * hit alt + F2 and type "uim-pref-gtk" to configure it
   * add either "uim-toolbar-gtk" or "uim-toolbar-gtk-systray" or none
of them (if you don't want any visual feedback in which mode you are
currently) to your startup programs in "gnome-session-properties"
   * restart your system
-----------------------------------------------------------------------------

---

### Post by catlett on 2006-07-28
Dont't know if this will help with the fonts but I thought I would post it just in case. [https://wiki.ubuntu.com/BetterCJKSupportSpecification/FontConfig?highlight=%28BetterCJKSupportSpecification%2FFontConfig%29](https://wiki.ubuntu.com/BetterCJKSupportSpecification/FontConfig?highlight=%28BetterCJKSupportSpecification%2FFontConfig%29)

---

### Post by Rastareefer on 2006-07-29
Anyone know the code for getting the Anthy status bar to appear and stay permanently on the desktop when in Japanese mode?
"uim-toolbar-gtk" works but when you close terminal it just disapears.

---

### Post by Hiroshima on 2006-07-31
I was going to ask the same thing, I want to switch from Skim to UIM, but am a little afraid since skim is working (but won't allow skype to open)

Cheers,

Hiroshima

---

### Post by Hiroshima on 2006-07-31
Ok, so you just follow what was here:
[http://ubuntuforums.org/showthread.php?t=189834&highlight=scim+setup+japanese](http://ubuntuforums.org/showthread.php?t=189834&highlight=scim+setup+japanese)

The important bit is to put the line in a "run command" box rather than a terminal.

Hit ALT+F2 to get a command box, put in the line
[COLOR="Red"]uim-toolbar-gtk [/COLOR] OR [COLOR="Red"]uim-toolbar-gtk-systray[/COLOR]

Next question, how to get that to go automatically at startup?

Cheers,

Hiroshima

PS, I'm going to be away from my computer for a month, so good luck!

---

### Post by Rastareefer on 2006-08-01
Thanks for the info.
However, I tried both commands and while they work durring the current session, the settings are lost on reboot.

Is there any way to save these settings so that the UIM switch is on the sys tray permanently?

---

### Post by catlett on 2006-08-02
In ubuntu you could add it to start-up inside "sessions" (or at least you "should" be able to)
Go to System<Administration<Sessions  when the window comes up, select "startup programs"
Select "add" and when the window opens with "enter command" enter the command you have been putting in "run command" box. I believe it is uim-toolbar-gtk-systray. Select "OK" and that application will start during the systems "start up". As long as the command that you were using in the "Run command" box is the one you entered, then the program will start because the command you entered is issued at startup.
Good luck.

---

### Post by Rastareefer on 2006-08-05
Any idea how to do this in Kubuntu?
There does not appear to be a session option in the control panel.

---

### Post by AiBo on 2006-09-08
I am currently using gnome, but like the KDE enviroment better.  My problem is that I need to use Chinese and English throughout the work day.  I have both desktop enviroments installed on my system, but gnome seems to handle Chinese a lot better.

Whenever I try to boot into KDE the Chinese that shows up in dialogs, text and menus in partial at best.  A charater or two is seperated by a . or center dot where a charater should be.  Has anyone encountered this type of problem?

Would love to get KDE up and running!

---

