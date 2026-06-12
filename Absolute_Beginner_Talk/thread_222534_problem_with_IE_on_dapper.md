---
title: "problem with IE on dapper"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by zarbov on 2006-07-25
hey there!
i'm new to linux and i was trying to install ie4linux on my ubuntu dapper 6.06 but with no success.

i installed wine + cabextract, and also ie4linux beta 10. i have an icon on my desktop, but everytime i try to open it, the window shuts down after a second (even less).

when i try to run ie6 from the bin folder insie the terminal i get the following message:
```
fixme:actctx:CreateActCtxW stub!
fixme:actctx:CreateActCtxW stub!
err:shell:ReadCabinetState Initializing shell cabinet settings
fixme:actctx:ActivateActCtx stub!
fixme:actctx:CreateActCtxW stub!
err:rebar:REBAR_WindowProc unknown msg 200b wp=00000000 lp=71180f00
fixme:actctx:CreateActCtxW stub!
fixme:toolbar:TOOLBAR_CheckStyle [0x200d8] TBSTYLE_REGISTERDROP not implemented
fixme:toolbar:TOOLBAR_CheckStyle [0x200d8] TBSTYLE_REGISTERDROP not implemented
fixme:shell:NTSHChangeNotifyRegister (0x200d8,0x00008003,0x00008000,0x0000c070,0x00000001,0x7fb9dc90):semi stub.
fixme:toolbar:TOOLBAR_Unkwn45D hwnd=0x200d8, wParam=0x00000000, size.cx=1024, size.cy=32000 stub!
fixme:toolbar:TOOLBAR_CheckStyle [0x200d8] TBSTYLE_REGISTERDROP not implemented
fixme:toolbar:TOOLBAR_CheckStyle [0x200d8] TBSTYLE_REGISTERDROP not implemented
fixme:toolbar:TOOLBAR_Unkwn464 hwnd=0x200ce wParam 00000001 lParam 00000000
fixme:toolbar:TOOLBAR_Unkwn45D hwnd=0x200ba, wParam=0x00000000, size.cx=1024, size.cy=764 stub!
fixme:shell:NTSHChangeNotifyRegister (0x200ba,0x00008003,0x0c02b7ff,0x0000c070,0x00000001,0x7fb9dcd0):semi stub.
err:rebar:REBAR_Layout no redraw and client is zero, skip layout
fixme:actctx:CreateActCtxW stub!
fixme:actctx:CreateActCtxW stub!
fixme:actctx:CreateActCtxW stub!
fixme:shell:NTSHChangeNotifyRegister (0x200e8,0x00008003,0x0003f5f4,0x00000410,0x00000001,0x7fb9ea88):semi stub.
fixme:shell:SignalFileOpen (0x00000000):stub.
fixme:hook:IsWinEventHookInstalled (32773)-stub!
```

i use ubuntu dapper drake 6.06 (gnome) + compiz + xgl , wine 0.9.9 , cabextract 1.1.

anyone have any idea what i did wrong?:-k 

thanks in advance!

---

### Post by rbalfour on 2006-07-25
> not implemented is the keyword here.
Not support might be another way at looking at...
Plenty of GOOD broswer out there. That work with Ubuntu.

---

### Post by zarbov on 2006-07-25
i'm sure there are very good browsers for linux. i use ff for most of the time. but i need ie to logon to my bank account (the web page wants ie only).

is there a browser that can fix that? i tried Opera but it doesn't work either. any suggestions?

---

### Post by bigken on 2006-07-25
I would install vmware and then windows wot ever 98/2000/xp then you have the whole windows thing inside ubuntu

---

### Post by psycosmyth on 2006-07-25
I'd sue the bank[-(

---

### Post by stig on 2006-07-25
> **psycosmyth said:**
> I'd sue the bank[-(

Agreed! My small business has accounts with three major UK banks. When I started on Linux about a year ago none of them let me get into my internet accounts using Linux - there were even difficulties on Windows with Firefox or Opera.

After pestering them and pointing out how out-of-date they were and how bad IE was for security they have now changed and all will allow me to get in using Firefox on Ubuntu 6.06

Some of the IT people in banks *like* you to complain because it helps them convince the accountants and directors that they need to move with the times. Some of the bank IT people told me they use Linux at home but could not use it at work.

If we don't put the pressure on, the banks won't change.

---

### Post by bigken on 2006-07-25
Must admit I agree the banks are behind the time but personaly ive never had any trouble with HSBC ;)

---

### Post by BoneKracker on 2006-07-25
Have you tried the Firefox extension called IE Tab?  Don't know if that will work, but it's a thought.

And you should definitely complain to the bank that they are not being standards-compliant.  Then get a new bank.  I did.

---

### Post by Arnaud_B on 2006-07-25
Just download a demo of crossover and install ie in it... I did it for my bank too and it works great :-)
you can complain if you wish but I think it's a lost of time... ;-)
Good luck!
A.

---

