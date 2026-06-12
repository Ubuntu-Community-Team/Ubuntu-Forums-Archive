---
title: "Can't type in Chinese =("
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by Villa on 2006-11-11
I'm a BIG Linux noob, I have no idea about any of the commands. =(


I've read many threads, and I've finally got SCIM working. I see the little taskbar down at the bottom of the screen, does that mean it's working?

So anyway I open up Text Editor for Ubuntu 6.10, turn on SCIM, but I don't know how to type in Chinese? Do I just type in the pinyin and press enter or something? I pressed ctrl+space and all the other commmands, but none of them seemed to change the pinyin I typed into the Chinese characters. =/

Any help appreciated! Thanks. =)

EDIT: I think I see how to do it now. =) But I'm having a problem. I don't have a keyboard with chinese strokes on them, and it doesn't bring up the right characters when I type in the pinyin. Which mode should I select? Plus, how do I use this on Firefox when typing in forums?

---

### Post by RAV TUX on 2006-11-12
moving to absolute beginner talk forum.

---

### Post by ezphilosophy on 2006-11-12
Could you give a bit more detailed information about your problem?  By the sound of your "edit", you got it working.  So, now it is just a problem of setting it up? 
When you get it installed, there's like 10 different input methods each for &#31616;&#20307; and &#32321;&#20307;.  If you want to type in standard pinyin, you will have to select it in the setup, or just keep hitting shift+ctrl until you get the right input method.

---

### Post by Villa on 2006-11-17
Ah ok cool thanks. So there are different input methods, and one pinyin method which I have to find? 

Another thing I'm not sure about is, do I need a keyboard with chinese strokes on them, or will a standard keyboard be fine? Whereabouts could I get these keyboards from, any store? (I live in Sydney, Australia)

Thanks. =)

---

### Post by Abiezer on 2006-11-17
The method I use to enter Chinese is called &#26234;&#33021;&#25340;&#38899; - it's the only option listed under 'Chinese (simplified)' entry that's named only in Chinese, perhaps that's why you missed it?
There's no need for a special keyboard - the only non-standard character used in pinyin (that occurs to me now, at least) is 'ü', and you simply substitute 'v' for that, e.g. to get &#22899; you type 'nv'.

---

### Post by Villa on 2006-11-17
Ah ok thanks very much. =) How do I type in Chinese in Firefox though?

EDIT: I checked out this thread, [http://www.ubuntuforums.org/showthread.php?t=25412&highlight=chinese]("a HOWTO")  but it doesn't open up SCIM when I press ctrl space in firefox. Plus, I don't know how to change the font to the one recommended? I copy pasted the code into the terminal, but it didn't work. =(

---

### Post by Abiezer on 2006-11-17
When the cursor's in a text area, I can hit Ctrl-Space to switch to Chinese input - I think it actually switches between default (in my case English) and whatever SCIM method you last used, so maybe you'll have to select pinyin manually one time.
To do that, again with the cursor in a text area, mouse over the SCIM icon (it's on the bottom right of my screen) and the menu bar pops up. If you click on the bit that says 'English/keyboard' you get a menu showing the available input options.

---

### Post by Villa on 2006-11-17
I can't see the SCIM icon for me, and when I hit ctrl-space nothing seems to happen.

Even in text documents pressing any of the shortcut keys doesn't work for me. THe only way I can change from english to other langugages is by right clicking, and selecting the input method using my mouse. And in firefox right clicking doesn't bring up an option to change the input method. Could it perhaps be because I'm lacking something that I should have installed earlier? (I didn't follow that particular guide and use all those commands, I don't know how to use the Cli. =()

Thanks for the help. =)

---

### Post by Abiezer on 2006-11-17
If you go to 'System-->Preferences' do you have an entry 'SCIM Input Method Setup'? There's a number of options to tinker with there, the most relevant being 'Panel > GTK' ( there's a checkbox there to enable 'Show tray icon') and 'FrontEnd > Global Setup'.

---

### Post by Villa on 2006-11-17
I've set up everything that you said, but I still don't know how to turn it on (besides right clicking in Text Editor)

What buttons should I press to turn on the SCIM input taskbar in Firefox and global programs? I don't understand the shift, keyrelease, etc. instructions they give. =(

EDIT: I think it's because I have no 'Turn on' trigger, but I don't know how to set it up. Trying to set up the hotkeys and keycode for 'turn on' etc. is confusing. I mash the keyboard but nothing changes. =(

---

### Post by Villa on 2006-11-17
I can now see the little chinese character (the SCIM toolbar I think) in the bottom right hand corner of my screen, but clicking on it or right clicking on it does nothing. It doesn't change to chinese output or anything. =(

---

### Post by Abiezer on 2006-11-18
I'm at a bit of a loss as to what's up then, Villa. 
The icon that appears on my desktop (Gnome, the 6.06 standard install) has the four letters 'SCIM' in two rows. Mousing over that brings up the tool bar. Not sure what you're seeing, unless you already have it set to enter Chinese.
I attach two screenshots from my SCIM setup, in case they might help. As you can see, I have no 'turn on' or 'turn off' shortcut set either, but seems to make no difference.

---

### Post by rigol on 2006-11-30
Same here - I can type chinese in gedit, but just when I use SCIM as input method from the right click dropdown menu. It seems the shortcuts aren't working?

---

### Post by flameproof on 2006-11-30
Follow this link:

[https://help.ubuntu.com/community/SCIM](https://help.ubuntu.com/community/SCIM)

Look specially for:

*Note : You should already be able to use SCIM input in a few applications, like gedit (Application>Accessories>Text Editor), by right clicking on the document, then selecting Input Methods>SCIM Input Method. However, it won't work in the others, like Open Office. *

..and read below it....

It works 100% - &#20320;&#26126;&#30333;&#25105;&#35828;&#20160;&#20040;&#65311;

For Firefox you don't have to do anything. After language support is installed it should display Chinese well. However, a few pages may have coding errors.

---

### Post by mhenriday on 2006-12-16
Well, **flameproof**, all I can say is **&#20160;&#20040;&#37117;&#19981;&#25026;** &#65281; As you can see from the copy of my SCIM-setup.desktop found at the very bottom of this message, I did manage to configure SCIM in some way, following the same instructions found in the link you posted above, but I can neither write Chinese or Japanese text in gedit by choosing the SCIM input method the right-click menu or by using CTRL+space or Shift+space (I presume here that the term 'space' refers to the space key at the bottom of a standard keyboard), nor have I been able use the latter two methods to import Chinese or Japanese text into an OOo document or the present letter. The only method I could use to write the Chinese text above was to go to a Southeast Asian web-based editor, type &#25340;&#38899; in there, copy the resulting graphs, and then paste here. What can I be doing wrong ? I tried to check my SCIM settings against those of **Abiezer**, but despite the fact that when I moused over each thumbnail I was told that I could obtain a larger image by clicking on it, nothing happened when I did so, and my eyues are no longer good enough to read directly from them. Talk about frustrating ! My SCIM settings are as follows (my apologies if the terminology isn't exact ; I'm translating from the Swedish, which is my Ubuntu default language) :

FrontEnd

General settings : Keyboard layout : Swedish (selected by me)
Show unconverted Latin letters in window (checked) (default)
Use same input method in all programmes (checked) (default)

Activation : Control+space,Shift+space,Zenkaku_Hankaku,Hangul
...
Next input method : Control+Alt+Down,Shift+Control+KeyRelease+Shift_L,Shift+Control+KeyRelease+Shift_R
Preceeding input method : Control+Alt+Up,Shift+Control+KeyRelease+Control_L,Shift+Control+KeyRelease+Control_R
Show menu with methods : Control+Alt+Right
(The above, of course, are all default settings)

IMEngines

General settings :
Installed input methods :
Latin letters
Japanese
Simplified Chinese
Traditional Chinese
Other
(all the above are checked ; selected by me)

Anthy :
Input mode : Hiragana (default)
Typing method : Romaji typing method (default)
Conversion mode : Multi segment (default)

Chewing :
Options : 'SpaceKey as selection key' checked (default)
Keyboard :
Trigger keys : Ctrl+space (default)
Chewing CHI/ENG keys : Shift+Shift_L+KeyRelease (default)
Number of Selection Keys : 9 (default)
Customized Selection Keys : 1234567890 (default)
Use keyboard type : Default Keyboard (default)
Decorative Color (default settings)

Smart Pinyin :
Auto combine phrase (checked) ... Max user phrase length : 8 (default settings)
Auto fill preedit (checked) ... Max preedit length : 32 (default settings)
Match longer phrase (unchecked) ... Smart match level : 20 (default settings)
Always show lookup table (checked) ... Burst stack size : 128 (default settings)
Show all keys (unchecked) ... Dynamic sensitivity : 6 (default settings)
Dynamic Adjust (checked) ... Save period (s) : 300 (default settings)
Save user data in binary format (unchecked) (default)

Pinyin :
Use tone (unchecked) default ... Allow incomplete pinyin (checked) (default settings)
Ambiguities (unchecked) (default)

Keyboard : (all default settings)

Generic table
Generic :
Show prompt (checked) (default)
Show key hint (checked) (default)
Save user table in binary format (unchecked) (default)
Show the user defined phrases first (checked) (default)
Show the longer phrases first (unchecked) (default)

Panel
GTK :
Show toolbar : Always (selected by me)
(All other settings default settings)

I should be most grateful for specific and detailed information in the event that there is anything in the above that requires changing in order to make importing Chinese and/or Japanese graphs possible using my keyboard. I am presently using **Ubuntu 6.10** on an old Pentium III with a clock speed of 498 MHz, 512 MB RAM, and two hard disks, with 19.5 GB and 129.5 GB capacity, respectively....

Henri

[Desktop Entry]
Encoding=UTF-8
Name=SCIM Input Method Setup
Name[cs]=Nastavení vstupní metody SCIM
Name[de]=Einstellungen der SCIM-Eingabemethoden
Name[fr]=Configuration de la Méthode de Saisie SCIM
Name[it]=Configurazione del metodo di inserimento SCIM
Name[ja]=SCIM&#20837;&#21147;&#12513;&#12477;&#12483;&#12489;&#12398;&#35373;&#23450;
Name[ko]=SCIM &#51077;&#47141;&#44592; &#49444;&#51221;
Name[pa]=SCIM &#2567;&#2672;&#2602;&#2625;&#2673;&#2591; &#2594;&#2672;&#2583; &#2616;&#2632;&#2591;&#2565;&#2673;&#2602;
Name[zh_CN]=SCIM &#36755;&#20837;&#27861;&#35774;&#32622;
Name[zh_TW]=SCIM &#36664;&#20837;&#27861;&#35373;&#23450;
Comment=Setup utility for Smart Common Input Method platform
Comment[cs]=Nástroj pro nastavení Smart Common Input Method platformy
Comment[de]=Einrichtungswerkzeug für die Smart Common Input Method-Plattform
Comment[fr]=Utilitaire de configuration de la plateforme "Smart Common Input Method"
Comment[it]=Programma di configurazione per il metodo inserimento comune intelligente
Comment[ja]=Smart Common Input Method platform &#12475;&#12483;&#12488;&#12450;&#12483;&#12503;&#12518;&#12540;&#12486;&#12451;&#12522;&#12486;&#12451;
Comment[ko]=&#46609;&#46609;&#54620; &#44277;&#53685; &#51077;&#47141; &#48169;&#48277; (SCIM)&#51012; &#50948;&#54620; &#49444;&#51221; &#54532;&#47196;&#44536;&#47016;
Comment[pa]=&#2616;&#2606;&#2622;&#2608;&#2591; &#2581;&#2622;&#2606;&#2600; &#2567;&#2672;&#2602;&#2625;&#2673;&#2591; &#2606;&#2632;&#2562;&#2597;&#2616;&#2593; &#2602;&#2610;&#2631;&#2591;&#2603;&#2622;&#2608;&#2606; &#2610;&#2568; &#2616;&#2632;&#2591;&#2565;&#2673;&#2602; &#2616;&#2617;&#2626;&#2610;&#2596;
Comment[zh_CN]=&#26234;&#33021;&#36890;&#29992;&#36755;&#20837;&#27861;&#24179;&#21488;&#30340;&#35774;&#32622;&#24037;&#20855;
Comment[zh_TW]=&#27867;&#29992;&#26234;&#24935;&#22411;&#36664;&#20837;&#27861;&#24179;&#21488;&#30340;&#35373;&#23450;&#24037;&#20855;
Exec=scim-setup
Icon=scim-setup.png
Terminal=false
Type=Application
StartupNotify=true
Categories=Applications;Settings;
X-Ubuntu-Gettext-Domain=scim

---

### Post by dj3 on 2008-05-12
I have two solutions:

I. Method: Go to "System"|"Administration" | "Language Support" (click). There at the bottom you should get to see "Input method". Select "activate the input method for complex characters" (Sorry, I don't remember the exact wording in English version of Ubuntu). Log in again. SCIM is activated.

In order to use the Chinese input method of your choice you might have to install some extra packages. I use Smart Pinyin. So I had to install "scim-pinyin" and "scim-tables-zh".

AND YOU ARE DONE! :)
------------------------------
II. Method (alternative, not optimal but it worked for me before): Install the packages mentioned above: "scim-pinyin" and "scim-tables-zh". You will also need "scim-bridge", "scim-GTK2-immodule".

 Open gEdit text editor and paste there

```

#!/bin/sh
export XMODIFIERS="@im=SCIM"
export GTK_IM_MODULE=scim-bridge
scim-bridge -d 

```

Save it in the hidden folder ".scim" in your home directory. Name the file "10scim". Now onen the Console and type

```

sudo gedit

```

Enter your password. Paste into gedit the following lines:

```

xport XMODIFIERS=@im=SCIM
export GTK_IM_MODULE=scim-bridge
scim-bridge -d

```

Save the file under "/etc/X11/Xsession.d", give the name "95input". Restart the X-server by pressing "Crl" + "Alt" + "Return" or just restart the system. By now everything should work. 

This method is a bit "painful" but it saved me my life on many some other, less comfortable distros than Ubuntu. :grin:

---

### Post by queenofbabes on 2008-05-14
I think I understand what is being said here, and SCIM does work fine in gedit, but I don't know how to actually start *typing in Chinese in other applications!*

For example in firefox I start typing in a text area, the SCIM toolbar is there all right, but I can't get it to the Chinese input mode. I can only type English...All the shortcut keys don't seem to work...

---

### Post by mhenriday on 2008-05-24
**Queen of babes**, I don't know what version of **Ubuntu** you are using, but if it's anything recent, I think you will be able to find the help you need on this [_SCIM documentation page_]("https://help.ubuntu.com/community/SCIM"). You might want to consider following the instructions there and then letting us know if with their help you succeeded in resolving your problem....

Henri

---

### Post by flameproof on 2008-06-03
> **mhenriday said:**
> **Queen of babes**, I don't know what version of **Ubuntu** you are using, but if it's anything recent, I think you will be able to find the help you need on this [_SCIM documentation page_]("https://help.ubuntu.com/community/SCIM"). You might want to consider following the instructions there and then letting us know if with their help you succeeded in resolving your problem....

Henri

According to the page you named System>Admin>Language Support should have a variety of language. The only language I can chose (8.04) is "english". 

So what now?

---

### Post by mhenriday on 2008-06-13
**Flameproof**, take a look at the screendump attached hereto, which shows a portion of the «Language Support» window on my machine. (If you compare it to the illustration in the tutorial to which I provided a link, you will not, I think, be confused by the fact that the language used therein is Swedish.) There are two important things to be understood from the picture - the first and most important, which for some reason (I suspect the illustration there displayed is quite old) is _not_ shown - but is mentioned - in the tutorial, being that in order to obtain support for CJK languages, among others, one must tick the little box at the bottom left under «Input Method», which activates support for the input of complex glyphs. Thereafter, one must scroll through the list of languages and tick the little box to the right of the language(s) for which one desires support. After following the above instructions, you should find **SCIM 1.4.7** working on your **Hardy** box. Report back and let us know how this works for you !...

Henri

---

### Post by single29 on 2008-07-11
I can type in Chinese as an user but not a root. What do I need to configure to enable root?
Thanks,
single29

---

### Post by mhenriday on 2008-07-13
**Single29**, I'm guessing here, but wouldn't one have to have configured the **Ubuntu** default language to Chinese (if that is possible) during installation, in order to type Chinese in as root ? What language is your default language in **Ubuntu** ?...

Henri

---

