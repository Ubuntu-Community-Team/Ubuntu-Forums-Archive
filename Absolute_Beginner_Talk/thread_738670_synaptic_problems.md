---
title: "synaptic problems"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by tropdoug on 2008-03-28
Hi guys,

I am trying to install the drivers to suit my Canon LBP 3200, as per the step by step instructions from here:- 

[COLOR=Blue]https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900[/COLOR]

Because I am running an amd64 bit system, I need to add the various [COLOR=Blue]ia32-lib[/COLOR] packages as mentioned right down the bottom of the install page. However when I use Synaptic to try to install 

[COLOR=Blue]ia32-libs-openoffice.org and ia32-libs-gtk[/COLOR] I get the following dialogue box, [COLOR=DarkOrange](attachment 1) [/COLOR]and then I click the mark button and get [COLOR=DarkOrange](attachment 2)[/COLOR] 

And then nothing happens. 

So I presume that even though these packages are in my list, they are actually not available from within the downloaded repositories, but my question is, how do I know where to get them from, and therefore what repositories to download? 

I currently have [COLOR=DarkOrange](attachment 3 & 4)[/COLOR] By the way, I have seen posts that include screen shots within the body of the message, and not as attachments, how do I do this please?

Thanks in advance

Douglas

---

### Post by mikeyphi on 2008-03-29
Then don't use Synaptic.....use the site mentioned in that guide, towards the bottom of the page - 
"One option is to download Edgy's ia32-libs-openoffice.org package from [WWW] here, and to install it manually"

The site seems to have the packages you need.

---

### Post by tropdoug on 2008-03-29
I am trying to follow the 64 bit instructions at the bottom of that page, but things are not going as they should, for instance 

[COLOR=Blue][I]'had to install following ia32 libraries in my Edgy amd64 distribution, I did this _using Synaptic,_ installed; **ia32-libs**, **ia32-libs-gtk**, [B]ia32-kde'

[/B][/I][COLOR=Black] I[/COLOR][COLOR=Black] tried to do this in synaptic, finding that ia32-libs and ia32-libs-kde are already installed, so I marked ia32-libs-gtk for installation and these dialogs come up (attachments 1 & 2) then it simply won't install. How do I know what are the required repositories? 

I don't understand what is happening, or why? if someone can help I would very much appreciate it, because if I cannot get my printers working (and I haven't even started on my wireless HP all in one yet) then linux will not be an option for me. [/COLOR]  
[/COLOR]

---

### Post by pieisgood4589 on 2008-03-29
> **tropdoug said:**
> I am trying to follow the 64 bit instructions at the bottom of that page, but things are not going as they should, for instance 

[COLOR=Blue][I]'had to install following ia32 libraries in my Edgy amd64 distribution, I did this _using Synaptic,_ installed; **ia32-libs**, **ia32-libs-gtk**, [B]ia32-kde'

[/B][/I][COLOR=Black] I[/COLOR][COLOR=Black] tried to do this in synaptic, finding that ia32-libs and ia32-libs-kde are already installed, so I marked ia32-libs-gtk for installation and these dialogs come up (attachments 1 & 2) then it simply won't install. How do I know what are the required repositories? 

I don't understand what is happening, or why? if someone can help I would very much appreciate it, because if I cannot get my printers working (and I haven't even started on my wireless HP all in one yet) then linux will not be an option for me. [/COLOR]  
[/COLOR]

Restart. I think that will fix the unresolved dependency issues- restarting clears the cache, so try again after the install.

---

### Post by tropdoug on 2008-03-29
I am going Bald! 

Ok, did the restart, added  edgy universe and edgy main into synaptic reloaded the repositories, the new list contains all the required packages, but same result when attempting to mark them for installation Soooo, went back to the web page, downloaded the ialibs32 packages direct from the mirror, tried to install using Gdebi package installer, and it tells me their is a newer package already installed, Next step download office .org also from mirror and then try to install. Dialog pops up telling me that the same package exists in something called a "Sofware Channel" and I should install from there. 

What and where is this 'software channel'?

---

