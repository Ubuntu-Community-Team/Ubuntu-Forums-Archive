---
title: "Theme Screenshot"
date: 2006-09-17
forum: Art &amp; Design
---

### Post by Super_6_4 on 2006-09-17
I'm trying my hand at building GDM themes, but I can't find any where that tells how to get the screenshot file (that actually works). Every place I look says to take the screenshot from the terminal - but I can't or don't know how.

Here's what I've tried:
1. Log of GUI so my Theme is displayed on VT 7
2. CTRL+ALT+F1 to get to tty1
3. logged in as my regular user (I have root-login disabled)
4. at the prompt, typed: **chvt 7 ; sleep 5 ; import -window root ~/screen.png -display :0.0 ; sleep 5 ; chvt 1**
5. cursed profusely at the errors displayed#-o 
6. retried step 4. with "sudo"
7. cursed even more profusely.#-o 

The errors I get are:
**import: unable to open X server `'.**
**import: missing an image filename ':0.0'.**

Can anyone help me?:confused:

---

### Post by s_h_a_d_o_w_s on 2006-09-17
you want to take a screenshot of your new-made gdm? Applications -> new login in nested window (not there by default, so alacarte), that'll log you in, but in a window. Then make it fullsreen and snip it down with gimp. ;-)

---

### Post by Super_6_4 on 2006-09-18
Thank you!!! I forgot to install the Xnest package before trying your advice - so I had some trouble, but after that it worked like a charm. Thank you!:biggrin:

---

### Post by s_h_a_d_o_w_s on 2006-09-19
No problem! Glad I could help!

---

### Post by graabein on 2007-02-27
> **Super_6_4 said:**
> Thank you!!! I forgot to install the Xnest package before trying your advice - so I had some trouble, but after that it worked like a charm. Thank you!:biggrin:

I'm on Xubuntu and have the same problems as you in your original post. I've installed **xnest** now but what is the launcher for it? I don't have **alacarte**.

---

### Post by frup on 2007-03-01
going out on a limb with no clue what so ever, what would doing window user instead of window root produce?

---

### Post by comorbid on 2008-02-09
Sorry to drag this up again, but not only am I getting the same error from trying to run the capture script, but Xnest also doesn't show my theme when I use New Login in a Window. It instead shows a big login box with the Debian logo, on top of the Human theme background color.

Is there a step I'm missing somewhere, or am I just gonna have to use the picture I took of my monitor with my camera? If it matters, I'm on Gutsy for AMD64.

---

### Post by exploder on 2008-02-09
Use xnest, this is the command to get the GDM Theme in a window.

gdmflexiserver --xnest

I open up Gimp first and set it to grab the window without the window decorations and set the delay for 10 seconds.

Open the terminal and type gdmflexiserver --xnest

click on grab in Gimp and press enter to run xnest, when the cross hair appears click on the displayed GDM theme to snap the image.

Save the image with the file type and name you need.

---

### Post by comorbid on 2008-02-09
> **exploder said:**
> 
gdmflexiserver --xnest

That gives me the exact same result as New Login in a Window. :/

I should probably point out that the Debian GDM window has a menu bar at the top, with "Theme" as one of the options, but no custom themes are listed.

---

### Post by exploder on 2008-02-09
Isn't that what you are trying to get a screenshot of?

---

### Post by comorbid on 2008-02-09
No, because Xnest doesn't show my theme running it from Applications or from the command line. It shows the attached file.

---

### Post by exploder on 2008-02-10
Are you running Ubuntu or a Ubuntu based system?

---

### Post by comorbid on 2008-02-10
Gutsy for AMD64.

---

