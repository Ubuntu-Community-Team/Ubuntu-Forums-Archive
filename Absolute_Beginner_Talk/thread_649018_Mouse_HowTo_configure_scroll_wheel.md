---
title: "Mouse HowTo configure scroll wheel?"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by esteckis on 2007-12-24
How do I configure my mouse scroll wheel to scroll more than 1 line at a time? I have tried the mouse configure options and that only allows how fast the mouse moves across the screen.

I really do not use the right scrollbar to scroll a page and use the mouse wheel to scroll. Is there a way to configure this?  I did a search at the forum and this question was asked back in 3/2005 with no reply?

I am using Ubuntu Gutsy 64 bit.

Thanks for your help :)

---

### Post by linuxwizard on 2007-12-24
Look over this

[https://help.ubuntu.com/community/ManyButtonsMouseHowto](https://help.ubuntu.com/community/ManyButtonsMouseHowto)

---

### Post by esteckis on 2007-12-25
I will give it a try.



Thank you again :)

---

### Post by Acunga on 2008-03-14
Can you post what exactly should be done to edit the wheel to jump 5-6 lines

---

### Post by smurphy_it on 2008-03-14
> **linuxwizard said:**
> Look over this

[https://help.ubuntu.com/community/ManyButtonsMouseHowto](https://help.ubuntu.com/community/ManyButtonsMouseHowto)

Thanks for this useful post.

---

### Post by Acunga on 2008-03-14
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "Auto"
        Option          "Buttons"               "9"
        Option          "ZAxisMapping"          "4 5"
EndSection
IS "Buttons" indicating the number of lines that the wheel should jump

---

### Post by wesley_of_course on 2008-03-14
Out of curiosity I checked mine in  about:config and it looks like this ;
                                                    
                                                       status     type        value
mousewheel.withnokey.numlines        default    integer      1
mousewheel.withnokey.sysnumlines   default    Boolean   True 
 
mousewheel.withnokey.numlines - I believe  this one slows it  

mousewheel.withnokey.sysnumlines     -    being true makes it system value in my case 3 lines.    Screenshot below , hope this helps.

---

### Post by Acunga on 2008-03-14
I still can't get it how to configure the wheel to scroll more than one lines.I have changed 
mousewheel.withnokey.sysnumlines to 10 and it doesn't work, i have changed 
mousewheel.withnokey.sysnumlines to false and it doesn't work.
I don't know what is about:config but I do know that this task seems to be too tricky for me

---

