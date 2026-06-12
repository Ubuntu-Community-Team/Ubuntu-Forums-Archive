---
title: "i wanna lanuch icon for &quot;My Computer&quot;"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by kadeep95 on 2007-01-20
I want the script to launch this icon for My Computer that when i click it, it show like this

[http://www.pic2us.com/postimage/getimage.php/is/0screenshot.png](http://www.pic2us.com/postimage/getimage.php/is/0screenshot.png)

i tried and tried,but i can't found anything

thanks! :D

---

### Post by Jose Catre-Vandis on 2007-01-20
Right Click on desktop
Select Launcher

(no quotes)
Enter "My Computer" for Name
Enter "My_Computer" for Description
Enter "nautilus computer:///" for command
Click on the icon button and scroll down to find Gnome_Computer.png
OK out

On desktop double click on your new icon

Job done

---

### Post by Tiede on 2007-01-20
go to the configuration editor.
Alt+F2 ->gconf-editor
in gconf, follow apps->Nautilus->desktop and check the computer_icon_visible box.

EDIT: Oops! Beaten to the punch](*,) . But I think my way is better 8-)

---

### Post by kadeep95 on 2007-01-20
yes it is!

Thanks! &#3586;&#3629;&#3610;&#3588;&#3640;&#3603;&#3588;&#3619;&#3633;&#3610;

---

### Post by ComplexNumber on 2007-01-20
> **kadeep95 said:**
> I want the script to launch this

[http://www.pic2us.com/postimage/getimage.php/is/0screenshot.png](http://www.pic2us.com/postimage/getimage.php/is/0screenshot.png)

i tried and tried,but i can't found anything

thanks! :D
i'm not entirely certain what that screenshot has to do with anything, but to answer the title of the thread, fire up gconf-editor, go Edit then Find in the menu, type in "nautilus"(don't tick the 2 tickboxes for this). if you click on apps/nautilus/desktop, you will see it in there.

---

### Post by kadeep95 on 2007-01-20
> **Tiede said:**
> go to the configuration editor.
Alt+F2 ->gconf-editor
in gconf, follow apps->Nautilus->desktop and check the computer_icon_visible box.

EDIT: Oops! Beaten to the punch](*,) . But I think my way is better 8-)



big thanks Tiede!
it can help me a lot..t.ttttttttttttttttttttttttttt

 :lolflag: :lolflag:

---

### Post by Tiede on 2007-01-20
You're welcome!!! :D

---

### Post by Jose Catre-Vandis on 2007-01-20
> **kadeep95 said:**
> yes it is!

Thanks! &#3586;&#3629;&#3610;&#3588;&#3640;&#3603;&#3588;&#3619;&#3633;&#3610;

I agree, and now I know :-)

---

