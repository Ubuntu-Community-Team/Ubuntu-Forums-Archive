---
title: "Officially posting from linux"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by fedja_b on 2007-09-21
Well guys, just as the title says, I'm officially posting this form my first Ubuntu installation. Everything went smoothly, and faster then say installation of microsoft office...  that says a lot doesn't it. Now I'm a little bit confused, I have a feeling I do not know what to do.  
I have a few questions. First of all, Ubuntu sees my windows partitions, and I can access them and everything, Windows does not see this partition. Why? Second are there any shortcuts for switching between workspaces, and showing the desktop? 
That will be all for now, thanks everyone for helping me out and being such a great community!

---

### Post by Dr Small on 2007-09-21
The switching between workspaces, should be in the bottom right corner, on the bottom bar, that allows you to have workspaces, and switch between them.

The reason windows can not see your Ubuntu partition, most likely, is because the Ubuntu partition is formated to ext3, a format which windows can not read.
Windows can read NFTS and FAT, of which your partition is neither.

Dr Small

---

### Post by argie on 2007-09-21
Other people have had success with this. I have not tried it myself: [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by qamelian on 2007-09-21
> **fedja_b said:**
> Second are there any shortcuts for switching between workspaces, and showing the desktop?

You can switch between workspaces by holding down Ctrl-Alt and pressing the left or right arrow keys to move left or right through workspaces.

---

### Post by fedja_b on 2007-09-21
Yes qamelian, thanks, that's what I needed ;) 
And for minimizing all windows and showing the desktop?

---

### Post by dpar on 2007-09-21
argie's link worked for me when I had windows. (Hard drive crashed and I lost it.)\\:D/

---

### Post by christhemonkey on 2007-09-21
EDIT: Am i really that slow at typing!
Ctrl+Alt+Right moves you to work space on the right and vice versa for Ctl+alt+left.

There is a button in the bottom left to show your desktop (there is probably a keyboard mapping for it as well)

As argie said, you can access your ubuntu drive using the driver from [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by qamelian on 2007-09-21
> **fedja_b said:**
> Yes qamelian, thanks, that's what I needed ;) 
And for minimizing all windows and showing the desktop?

I'm not sure about the "Show Desktop" bit. I'm sure that Gnome will let you map a key to it somewhere in your keyboard settings, but I don't see a default mapping. I'm 99% sure that there is a key mapping for it if you are using the "Show Desktop" plugin for Compiz / Beryl /Compiz-fusion, but that isn't terribly helpful if you don't use them! Wish I could be more help but I'm at work now and chained to Windows instead of my Linux box at home.:(

EDIT: I found your answer in the documentation on the Gnome website:

**Global Shortcut Keys**

   Global shortcut keys enable you to use the keyboard to perform tasks     related to your desktop, rather than tasks on the currently selected window     or application.  The following table lists some global shortcut keys:
       Shortcut Key
 Function
    **Alt**+**F1**
 Open the **Applications Menu**.
   **Alt**+**F2**
 Display the **Run Application**               dialog.  See [the section called &#8220;Running Applications&#8221;]("http://www.gnome.org/learn/users-guide/latest/tools-run-app.html") for more               information.
                    **Print Screen**               
 Take a screenshot of the entire desktop.  See               [the section called &#8220;Taking Screenshots&#8221;]("http://www.gnome.org/learn/users-guide/latest/tools-screenshot.html") for more information.
   **Alt**+**Print Screen**
 Take a screenshot of the currently focused window.
   **Ctrl**+**Alt**+**Arrow keys**
 Switch to the workspace to the specified direction of the               current workspace.  See [the section called &#8220;Workspaces&#8221;]("http://www.gnome.org/learn/users-guide/latest/overview-workspaces.html") for               more information on working with multiple workspaces.
   [COLOR=Red]**Ctrl**+**Alt**+**D**[/COLOR]               
 [COLOR=Red]Minimize all windows and give focus to the desktop.[/COLOR]
   **Alt**+**Tab**
 Switch between windows.  A list of windows that you can               select is displayed. Release the keys to select a window.  You               can press the **Shift** key to cycle through the               windows in reverse order.
   **Ctrl**+**Alt**+**Tab**               
 Switch the focus between the panels and the desktop.               A list of items that you can select is displayed.  Release the               keys to select an item.  You can press the **Shift**               key to cycle through the items in reverse order.

---

### Post by livingtarget on 2007-09-21
Ctrl+Alt+D works for me to show the desktop, I think that's a default one but not sure.

---

### Post by bapoumba on 2007-09-21
> **livingtarget said:**
> Ctrl+Alt+D works for me to show the desktop, I think that's a default one but not sure.
Yep, with both GNOME and Xfce (don't know for KDE).

And congratulations to the OP!

---

### Post by fedja_b on 2007-09-21
Thanks very much for your help. I just have one more question and I'm on my way, promise. How do I find applications that I install. What is the equivalent of Start - All Programs in Ubuntu? Specifically I've installed foobar2k using wine. Now how do I run it???

---

### Post by bodhi.zazen on 2007-09-21
If you are looking for a button, like windows, to show your desktop :

right-click on on your panel (on a open space) -> select "Add to Panel"-> Actions-> Show Desktop

is that what you wanted ?

---

