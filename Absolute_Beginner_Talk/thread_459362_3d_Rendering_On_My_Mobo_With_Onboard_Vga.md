---
title: "3d Rendering On My Mobo With Onboard Vga"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by steve-shinn on 2007-05-30
Hi,

I have recently installed Ubuntu Feisty 7.04 i386 on my Pc which has the following mobo with onboard graphics :- Asus K8V-VM socket 754 ..... [http://uk.asus.com/products.aspx?l1=3&l2=14&l3=276&l4=0&model=1189&modelmenu=2](http://uk.asus.com/products.aspx?l1=3&l2=14&l3=276&l4=0&model=1189&modelmenu=2)

How do I check to see if 3D rendering is working (I'm pretty certain that it's not) and if it's not, what do i need to do to install the appropriate graphic drivers ?/

thks in advance

SteveS

---

### Post by ajgreeny on 2007-05-30
In terminal type:-
glxinfo

In the output, somewhere near the top there will be a statement like this if you have it working:-


name of display: :0.0
display: :0  screen: 0
**direct rendering: Yes**
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    
If not then you will need to looka bit further, I'm afraid.  Probably a different graphic driver.

---

### Post by steve-shinn on 2007-05-30
Hi,

This is the result of typing glxinfo :-


name of display: :0.0
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  16
  Current serial number in output stream:  17

Any suggestions as to what I now need to do ?? thanks in advance.

SteveS

---

### Post by steve-shinn on 2007-05-31
I'm just wondering if it wouldn't be easier to buy a cheap Nvidia graphics card ?

---

