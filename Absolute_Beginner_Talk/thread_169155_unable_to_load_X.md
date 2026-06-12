---
title: "unable to load X"
date: 2006-05-02
forum: Absolute Beginner Talk
---

### Post by e1ektrob0y on 2006-05-02
i was just given a ubuntu live cd and when i boot up, everything goes fine until a message that comes up that says unable to load X. something to do with graphics server. anyway it doesn't start afetr that. i'm completely new to linux and am wondering how to fix this problem. thanks.

---

### Post by chriscando on 2006-05-02
You might want to look into the boot options when you start up with the CD. See if you can try different settings reguarding the video mode. Sounds like it is not detecting your proper video settings.

---

### Post by e1ektrob0y on 2006-05-02
[QUOTE=chriscando]You might want to look into the boot options when you start up with the CD. See if you can try different settings reguarding the video mode. Sounds like it is not detecting your proper video settings.[/QUOTE]
yep i figured that but it all looks foreign to me cause i've always been a windows user. what settings would you suggest looking at?

---

### Post by e1ektrob0y on 2006-05-02
well i tried again and checked the log. i have a nvidia 7600gt and there was a long list of nvidia cards and my card was not on the list. would i be correct in assuming that ubuntu 5.04 doesn't support 7 series nvidia chipsets? 

anyway these are the errors i got:
"/user/x11rg/lib/modules/extensions/libGLcore.a:m_debug_clip.0" no symbols found
and then," " " " " " " " "debug_norm.0" no symbols found
             " " " " " " " " "debug_xform.0" no symbols found
EE: no devices detected fatal server error: no screens found.
does that sound like my video card is not supported? thanks

---

### Post by chriscando on 2006-05-04
When you boot with the CD it first prompts you with what options to use, I can't remember what they are but see if there is a help menu and look for something concerning video. I bet your card will work just fine, its just not getting detected correctly.

Sorry for being vague, if your having trouble I'll try it myself and post up more details.

---

