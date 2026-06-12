---
title: "Separator lines in Gtk themes"
date: 2007-12-19
forum: Art &amp; Design
---

### Post by urukrama on 2007-12-19
I'm creating a new Gtk theme at the moment. All is nearly done, but there is one thing I can't figure out. 

In the first screenshot below you'll see the separator lines that are found in all Gtk themes. I have marked them with a dark asterisk (*). Is there a way of making those disappear? 

I've tried adjusting many different settings in the gtkrc file, but haven't had any luck so far. I know that if I created a pixmap or other image based theme I could easily circumvent this problem, but I don't want to do so. 

As far as I know, the colour of these lines cannot be set in the gtkrc file; their colour does not correspond to any colour settings in the theme file. I am using the rezlooks engine, but I have not seen any text-based gtk theme (using rezlooks, murrine, clearlooks, ubuntu-looks, etc.) where these lines are not visible.

I know I can change the xthickness and ythickness at the head of the file to 0, but that makes only some lines disappear -- those marked with a pink asterisk in the first screenshot, as seen in the second screenshot. I tried adjusting the x- and ythickness of individual widgets in the theme file, but without the hoped success.

So, is there a way to make those lines disappear?

---

### Post by smartboyathome on 2007-12-19
I think those are hardcoded in there if you can't ake them dissapear using x and ythickness.

---

### Post by AlexR1 on 2007-12-19
If you have pixbuf engine installed, you can use it to make those lines disapear,make it file linerc and put it in your theme directory, and in your gtkrc add line include "linerc", I don`t think that this will slow rezlooks engine, it is too small and can make it to get result you are looking for.

---

### Post by urukrama on 2007-12-20
> **AlexR1 said:**
> If you have pixbuf engine installed, you can use it to make those lines disapear,make it file linerc and put it in your theme directory, and in your gtkrc add line include "linerc", I don`t think that this will slow rezlooks engine, it is too small and can make it to get result you are looking for.

Thank you, but what would I put in that linerc file?

---

### Post by AlexR1 on 2007-12-20
Please disregard my earlier answer, i just tried with clearlooks engine and I am unable to remove those lines,sorry.

---

