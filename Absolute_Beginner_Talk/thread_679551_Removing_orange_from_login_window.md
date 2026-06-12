---
title: "Removing orange from login window"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by sayakb on 2008-01-27
Hello all
First of all, I have transformed my PC to gray shades. I have the Linux Mint login screen but I have converted the green background to gray. But during logon, when I click on my username, the selection color is orange. All other dialogs during logon (like change session etc.) are in shades of orange. How do I change this orange color?

---

### Post by swoll1980 on 2008-01-27
```
sudo gedit /etc/gdm/PreSession/Default
``` look for line that says default value 
you have to use binary so black would be #000000

---

### Post by sayakb on 2008-01-27
> **bloor75 said:**
> ```
sudo gedit /etc/gdm/PreSession/Default
``` look for line that says default value 
you have to use binary so black would be #000000

But that would be the background color that appears after logon and before the desktop loads. You may change that even from System -> Administration -> Login Window -> Local -> Background color

I want to change the selected objects color (Refer to System -> Preferences -> Appearance -> Customize -> Colors and change the "Selected Items" color. This would change the selected items' color for GDM. I want to change the sel items color in my login window)

---

### Post by AnonCat on 2008-01-27
A bug in Ubuntu prevents you from changing that color using the normal tools.  What you need to do to change the background color is to first load the "Login Window Preferences" program under System/Administrator.  Then click on the "background color" option and change it to what you want.   Copy down those numbers that appear in the "color name" box.  Now here are the steps:

1. Open the terminal and type:

sudo gedit /etc/gdm/PreSession/Default

2. Scroll down in the file that opens until you find this segment near the very bottom (yours will look a little different because mine has been edited:

# Default value
 	if [ "x$BACKCOLOR" = "x" ]; then
 		BACKCOLOR="x"
 	fi

	"$XSETROOT" -cursor_name left_ptr -solid "$BACKCOLOR"
fi

exit 0

3. Paste the value you took from the color box and paste it in place of where the "x" appears after the second "BACKCOLOR="x" code above.  Note, for you x will be some numbers and letters. 

4. Save the file and reboot

---

### Post by sayakb on 2008-01-27
> **AnonCat said:**
> A bug in Ubuntu prevents you from changing that color using the normal tools.  What you need to do to change the background color is to first load the "Login Window Preferences" program under System/Administrator.  Then click on the "background color" option and change it to what you want.   Copy down those numbers that appear in the "color name" box.  Now here are the steps:

1. Open the terminal and type:

sudo gedit /etc/gdm/PreSession/Default

2. Scroll down in the file that opens until you find this segment near the very bottom (yours will look a little different because mine has been edited:

# Default value
 	if [ "x$BACKCOLOR" = "x" ]; then
 		BACKCOLOR="x"
 	fi

	"$XSETROOT" -cursor_name left_ptr -solid "$BACKCOLOR"
fi

exit 0

3. Paste the value you took from the color box and paste it in place of where the "x" appears after the second "BACKCOLOR="x" code above.  Note, for you x will be some numbers and letters. 

4. Save the file and reboot

Already tried. Here's how mine looks:

	# Default value
 	if [ "x$BACKCOLOR" = "x" ]; then
 		BACKCOLOR="#A3A3A3"
 	fi

This is the code for gray color.. Still I get some orange shades.. :(

---

### Post by AnonCat on 2008-01-27
I'm surprised that didn't work for you.  I managed to change all of the orange backgrounds to blue in mine and I might be forgetting something, I'll dig around and get back to you.

---

### Post by sayakb on 2008-01-29
> **AnonCat said:**
> I'm surprised that didn't work for you.  I managed to change all of the orange backgrounds to blue in mine and I might be forgetting something, I'll dig around and get back to you.

Well, actually it changes the background color very well, but doesnt change the selected items (highlight) color.. Weird :(

---

