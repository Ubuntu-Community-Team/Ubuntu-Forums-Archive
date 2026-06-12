---
title: "Windows Key - Feisty &quot;How to make best shortcut uses with it?&quot;"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by MozartlovesUbun2 on 2007-09-01
Windows Key - Feisty "How to make best shortcut uses with it?"

I didn't ask for it, but my keyboard came with a "windows key" and being a once upon a time windows user, I'm used to using it for shortcuts, but feisty makes no use of the key, or I havn't found  one yet, so well I got this extra key and so how do I make use of it?

Also I have Compiz/Fusion running, so would that help  in anyway?
(Um also would anyone know of an up to date simple Compiz/Fusion users manual)

thanks

---

### Post by dsauxier on 2007-09-01
I actually have what I call a "linux patch" for the windows key.
First (and this step is VERY important), I printed the ubuntu logo onto a sticker and placed it over the windows key.

Then under System->Preferences->Keyboard Shortcuts, I mapped the key to "Show the Panel Menu"

---

### Post by Zootropo on 2007-09-01
With Compiz Fusion go to System -> Preferences -> CompizConfig Settings Manager, General Options, Commands

---

### Post by MozartlovesUbun2 on 2007-09-01
> **Zootropo said:**
> With Compiz Fusion go to System -> Preferences -> CompizConfig Settings Manager, General Options, Commands

hehe, nice thought but I've already made sure that nasty windows logo is covered,

hmm, I'ld like a bit more than just "Show the Panel Menu", like make it able to use in combination with other keys kinda thing, like:

1.show desktop

2.open home folder

3. etc...

thx

---

### Post by oomingmak on 2007-09-01
> **dsauxier said:**
> I actually have what I call a "linux patch" for the windows key ..... under System->Preferences->Keyboard Shortcuts, I mapped the key to "Show the Panel Menu"

> **MozartlovesUbun2 said:**
> hmm, I'd like a bit more than just "Show the Panel Menu", like make it able to use in **combination** with other keys kinda thing, like:

1.show desktop

2.open home folder

3. etc...

Why not just do both at the same time? that's what I do.


Go to: **System > Preferences > Keyboard > Layout Options > Alt/Win Key Behaviour** and set '*Meta is mapped to left Win key*'.

[IMG]http://i219.photobucket.com/albums/cc48/0omingmak/Screenshot-KeyboardPreferences.png[/IMG]


Then go to **System > Preferences > Keyboard Shortcuts** and define the key combinations you'd like to use.

Examples:

To set '**Show Desktop**' to Win key + D (i.e. the same as in Windows) scroll down the Keyboard Shortcuts 'Action' list to the 'Show Desktop' entry (it's under the 'Window Management' section), click on it and press the Win key and the 'D' key at the same time. The display will change to show "Mod4+D" (Mod4 is just the Linux name for the Win key).

Do the same for any other shortcuts you want to change - for example: To close a window by using Win Key + X, set the 'Close Window' action to Mod4+X.

You can then use the **Left Win key** in combinations with other keys (to show the desktop or close a window or whatever) while _*still*_ being able to use the **Right Win key** in a  similar manner to a  "Start Menu" key (because you can map the right Win key so that it opens the Main panel 'Applications' menu).



[COLOR=DimGray][COLOR=Black] Note: While this method is fine in principle, the actual implementation of keyboard shortcuts in Ubuntu is pretty flaky and crappy. It mostly works, but you will find certain key combinations refusing to work for no apparent reason (e.g. I tried to set my 'Home' folder to open using the Win Key + Home key, but that combination won't work. However, if I set it to Alt key + Home key, then for some strange reason it *does* work).

I don't think this problem is anything to do with the use of the Win key though, because I have other key combos that have nothing to do with the Win key at all, and they too are very temperamental, sometimes working and sometimes not (despite the fact that no settings have been changed)[/COLOR] .[/COLOR]

---

### Post by BobCFC on 2007-09-01
I have heard people are happy using xbindkeys and xbindkeys-config to set the multimedia keys etc maybe you could investigate.

 [http://ubuntuforums.org/showthread.php?t=79560](http://ubuntuforums.org/showthread.php?t=79560)

---

### Post by MozartlovesUbun2 on 2007-09-01
cool thanks, never looked in there before "System > Preferences > Keyboard > Layout Options > Alt/Win Key Behaviour"

I don't really know what a super key is, would anyone know what the default "Super key" is in CompizFusion? it shows up there a lot, i have no idea how to use it.

---

### Post by oomingmak on 2007-09-01
> **BobCFC said:**
> I have heard people are happy using xbindkeys and xbindkeys-config to set the multimedia keys etc maybe you could investigate.
I've already tried that. 

It's just as flaky and unreliable.

---

### Post by oomingmak on 2007-09-01
> **MozartlovesUbun2 said:**
> cool thanks, never looked in there before
You're welcome.

---

### Post by sailor2001 on 2007-09-01
superkey is your windows key on a qwerty board.....compiz uses that a lot in defaults, but you can usually change defaults to whatever you want in the key bindings

---

### Post by FuturePilot on 2007-09-01
There's tons of stuff you can do with it in Beryl.

---

### Post by airflow on 2007-09-13
I would like to use the shortcut-functions of Ubuntu/Gnome, but I can't get them to work properly. E.g., I would like to map the "Home Folder" (Nautilus) to <super>E (like in Windows), and the Terminal to <super>S.

Both programs (Natilus and Terminal) are available in Gnome/System/Preferences/Keyboard_Shortcuts, but when I want to set the shortcut for it, I already fail. As soon as I touch the Windows-Button (which is the <super>-button), the shortcut-manager already fills in <super>L. I never really can press the combination of buttons, pressing the <super>-button only already triggers that.

The layout-option setting in the keyboard-preferences of Gnome is set to default (Alt/Win key behaviour). I tried to set it to different settings, but it didn't help.

Any idea on how to get this simple task to work?

Thanks in advance,
airflow

---

### Post by wireddad on 2007-09-13
> **FuturePilot said:**
> There's tons of stuff you can do with it in Beryl.
 
How please?

---

### Post by airflow on 2007-09-15
> **airflow said:**
> Any idea on how to get this simple task to work?

I had problems with the built-in gnome tool to create own shortcuts. I assume it has to do with the fact that I don't use metacity as a windows-manager, but compiz. You can create the shortcuts via using the gconf-editor. This application is comparable to the regeditor in Windows. Start it (<Alt>+F2 and type gconf-editor) and edit the keys in /apps/compiz/general/allscreens/options.

Example of putting the file-manager nautilus to <the button with the flag> + E:
```
command0: nautilus
run_command0_key: <Super>E
```

bye,
airflow

---

### Post by Mogul345 on 2007-10-24
I'm trying to accomplish the same thing that most people here are trying to do, which is map winkey shortcuts to mimic what they do in windows. I've managed to get Win-D to minimize to desktop, Win-R to open the run app dialog, and Win-T to get the terminal up. However, I can't get Win-L to lock the screen, nor can I get Win-E to take me to my home folder.

Poking around in gconf-editor, I've found that the two that I can't get working are under /apps/gnome_settings_daemon/keybindings, whereas the ones that do work are under /apps/metacity/global_keybindings.

I don't know if this helps anyone, but I thought I'd share. I'm new at this Linux thing, but I like it alot so far!

EDIT:
So I figured out how to get the home folder working! in gconf-editor, go to /apps/metacity/global_keybinding_commands. Then for one of the commands, make the value *nautilus*. Then go to /apps/metacity/global_keybindings and for the corresponding run_comand key make the value be <Mod4><Hyper>e, and then you should be all set!

Now, the next question is, what is the command to lock the screen? Because that could be set up the exact same way I would reckon.

---

### Post by NT4usB on 2007-10-24
I use the heck out of the windows key in Windows. 
Tried to get the same in Ubuntu but could only configure the windows key by itself... no windows+<somekey>  so it's terminal for now.
Going to go back through this thread and learn how to set it up properly to get Nautilus with win+e, terminal from win+r, win+m for desktop, etc...
ed: wonder if I can get the right Ctrl+Alt+<left arrow/right arrow> combo to change desktops (for one handed operation)? 
It seems only the left set of Ctrl+Alt (+arrows) switches, and that takes two hands.

---

