---
title: "High Contrast Black - Ubuntu Installation"
date: 2009-08-19
forum: Assistive Technology &amp; Accessibility
---

### Post by zane.sims on 2009-08-19
Greetings everyone,

I am new to the Ubuntu forums, but have been using Ubuntu for a little while now.  Due to my visual impairment and issues I have had with Ubuntu having no High Contrast Black theme during installation, I was prompted to post the idea on Ubunu Brainstorm:

[http://brainstorm.ubuntu.com/idea/21111/](http://brainstorm.ubuntu.com/idea/21111/)

I thought that I would post the issue here in hopes that more people will be educated about this need.  Also, if anyone has any questions or if clarification need be made on the issue, please let me know.

Thanks!
Zane

---

### Post by arky on 2009-08-24
Can you mention what problems you face with the existing High Contract theme. Perhaps another work around would be a provide a keyboard switch that will toggle this.

---

### Post by arky on 2009-08-24
Workaround
----------

Go to System > Perferences > Appeareance and select darkroom 

Or run this command in a terminal 

gconftool -s -t string /apps/metacity/general/theme DarkRoom

---

### Post by zane.sims on 2009-08-24
Hello,
 
I appreciate your response, but that is not my problem.  Once I get the system fully installed, I am easily able to setup a high contrast black system theme.  My problem is that the INSTALLER for Ubuntu only offers high contrast white theme.  The high contrast white theme is VERY VERY bright for people with my eye condition and I liken it to looking into the sun.
 
Though perhaps I am missunderstanding you as well.  Is there a way to access a system menu in the installer or are you simply refering to the regular system menu for the installed system?  Hope this clarifies the issue.
 
Thanks!
Zane

---

### Post by arky on 2009-08-24
The High Contrast Installation actually uses the standard themes which can be changed with the following command.

gconftool -s -t string /apps/metacity/general/theme <theme-name>

Also I have made the same suggestion in the brainstorm idea.

---

### Post by zane.sims on 2009-08-24
Thanks again for your reply.  The solution you have provided may work, and I will use it in the meantime, but I still find that my solution has the added benefit of helping new ubuntu users who need this theme and are not as likely to know or understand cammands.  For new Ubuntu users, finding this command alone could be difficult.  They would not know what they are looking for.  I feel that if a high contrast option is to be offered on the menu, catching both ends of the spectum (bright & dark) would cover a great deal of visual impairments and make the change very easy and accessible for both the new and experienced user.
 
Thanks for your input,
Zane

---

### Post by arky on 2009-08-25
Zane perhaps we can file a wishlist to make 'High Contrast Inverse' the default theme for low-vision installation mode. Do you think that High Contrast Inverse would be a good choice for people with your eye condition.

---

### Post by zane.sims on 2009-08-25
I am not sure what you mean by "low vision installation mode".  Is this separate from choosing one of the accessibility options at the start of the installation?  If you mean for the accessibility menu option, then not exactly.  Just as I need the High Contrast Inverse, there are others with eye conditions that act in the opposite manner and need High Contrast (black on white).  After working with a variety of Visual Rehabilitation Specialists for various needs of my own, I have come to realize that it is important to cover both ends of the spectrum by providing both options.  Whether they need a very bright theme or dark theme, both optioins could be easily found at the start of the installation by pressing the function key associated with the accessibility menu.
 
Thanis again!

---

