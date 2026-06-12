---
title: "Internet Explorer Problem"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by xunshirine on 2006-12-06
Hello. I installed IE using ie4linux tool. It nows work great. But to install Babylon, it requires an internet explorer installation on drive_c. So I installed IE6 SP1 with wine but when try to start it , I just get a blank window. What might be the problem and how can be solved? Thanks

---

### Post by seshomaru samma on 2006-12-06
Run IE6 from the terminal and post the errors.

---

### Post by xunshirine on 2006-12-07
Hello. I tried to cd into the Internet Explorer directory via terminal but it doesnt work . My path is 

> /home/user/.wine/drive_c/Program Files/Internet Explorer
Those spaces between Program Files and Internet Explorer may cause problem. When try to cd into that directory , terminal can't find the path. So I can't execute IE from terminal. I also tried **open using terminal** option but it also didn't work. When double click the icon, it opens up with wine but just a blank window seen. I think I must configure the wine. But I couldn't find a neat and comprehensive guide for this.

---

### Post by scrooge_74 on 2006-12-07
> **xunshirine said:**
> Hello. I tried to cd into the Internet Explorer directory via terminal but it doesnt work . My path is 


Those spaces between Program Files and Internet Explorer may cause problem. When try to cd into that directory , terminal can't find the path. So I can't execute IE from terminal. I also tried **open using terminal** option but it also didn't work. When double click the icon, it opens up with wine but just a blank window seen. I think I must configure the wine. But I couldn't find a neat and comprehensive guide for this.

From the terminal use the "\" key and then give the space it will recognize it

---

### Post by ButteBlues on 2006-12-07
cd "/home/user/.wine/drive_c/Program Files/Internet Explorer" will work.

---

### Post by xunshirine on 2006-12-07
> **scrooge_74 said:**
> From the terminal use the "\" key and then give the space it will recognize it
Thanks. Yours worked.

> libGL warning: 3D driver claims to not support visual 0x5b
fixme:shell:StopWatchMode () stub!
fixme:shdocvw:IEWinMain "" 10
libGL warning: 3D driver claims to not support visual 0x5b
fixme:ole:CoResumeClassObjects stub
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x18a724)->((null) 1 0x33fb1c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x18a724)->((null) 25 2 0x33fb30 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x18a724)->((null) 26 2 0x33fb30 (nil))
fixme:shdocvw:ClDispatch_Invoke (0x18a724)->(-709 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33fa74 0x33fac0 (nil) 0x33fa84)
fixme:shdocvw:ClDispatch_Invoke (0x18a724)->(-5512 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33fa34 0x33fa80 (nil) 0x33fa44)
fixme:shdocvw:ClDispatch_Invoke (0x18a724)->(-5501 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33fa74 0x33fac0 (nil) 0x33fa84)
fixme:shdocvw:ClDispatch_Invoke (0x18a724)->(-5512 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33fa34 0x33fa80 (nil) 0x33fa44)
fixme:shdocvw:ClDispatch_Invoke (0x18a724)->(-5502 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33fa74 0x33fac0 (nil) 0x33fa84)
fixme:shdocvw:ClDispatch_Invoke (0x18a724)->(-5513 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33fa74 0x33fac0 (nil) 0x33fa84)
fixme:shdocvw:ClDispatch_Invoke (0x18a724)->(-726 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33fa74 0x33fac0 (nil) 0x33fa84)
fixme:shdocvw:ClientSite_GetContainer (0x18a724)->(0x33fb5c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x18a724)->({000214d1-0000-0000-c000-000000000046} 37 0 0x33fc80 (nil))
fixme:shdocvw:ClDispatch_Invoke (0x18a724)->(-5502 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33fb44 0x33fc70 (nil) 0x33fb54)
fixme:shdocvw:ClDispatch_Invoke (0x18a724)->(-5501 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33fb44 0x33fc60 (nil) 0x33fb54)
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x18b578)->(L"" L"" 0 0x33fc94)
fixme:shdocvw:BindStatusCallback_GetBindInfo (0x18b578)->(0x33fc98 0x33fbbc)
err:urlmon:URLMonikerImpl_BindToStorage InternetCrackUrl failed: 87
fixme:shdocvw:ClOleCommandTarget_Exec (0x18a724)->((null) 29 2 0x33fcc0 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x18a724)

This is the terminal data. Thanks

---

### Post by zetetic on 2006-12-08
I wonder why do people install Internet Explorer on Linux, giving the fact that even the Windows users know IE is pure crap and they are switching to other web browsers, lika Firefox.

zetetic

---

### Post by xunshirine on 2006-12-08
> **zetetic said:**
> I wonder why do people install Internet Explorer on Linux, giving the fact that even the Windows users know IE is pure crap and they are switching to other web browsers, lika Firefox.

zetetic

Some people addictive to adrenalin @zetetic. For many, there isn't any  alternative to feel the highest adrenalin as you do while you browse the web   via IE and viruses tickle you. Ok formal answer, cause for web design and some sites requires only IE to view.

---

### Post by houstonbofh on 2006-12-08
> **xunshirine said:**
> Hello. I tried to cd into the Internet Explorer directory via terminal but it doesnt work . My path is 

I know you solved this but also try command completion.  for example, from drive_c type "cd Progra" and hit the tab key, and "m\ Files" will magically attach to the end.

As to the first question, you will need all of the dll's wine doesn't do quite right.  Either copy the ies4linux config, or take apart the scripts.

---

### Post by xunshirine on 2006-12-08
> **houstonbofh said:**
> I know you solved this but also try command completion.  for example, from drive_c type "cd Progra" and hit the tab key, and "m\ Files" will magically attach to the end.

As to the first question, you will need all of the dll's wine doesn't do quite right.  Either copy the ies4linux config, or take apart the scripts.
Thanks for the reply @houstonbofh . From where I can copy ies4linux config?

---

### Post by houstonbofh on 2006-12-08
> **xunshirine said:**
> Thanks for the reply @houstonbofh . From where I can copy ies4linux config?
Not sure yet as I still have to do this myself.  If you follow the icons, you find /home/$user/.ies4linux/drive_c/ and I would start there.

---

### Post by quarkhirad on 2006-12-08
> **zetetic said:**
> I wonder why do people install Internet Explorer on Linux, giving the fact that even the Windows users know IE is pure crap and they are switching to other web browsers, lika Firefox.

zetetic

I absolutely agree with u. Infact even on windows i only use mozilla firefox 2.

I am sorry i dont want to hurt anybody but how can u want to run something as crapy and pathetic as IE7 in linux.HELP](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by houstonbofh on 2006-12-08
This IE bashing is highly innapproiate, and unhelpfull.  If you don't consider a job with IE only websites, or a education with IE only testing to be a good reason, that is your choice.  But don't bring it in here where someone chose differently than you.  The fact is that Ubuntu **Can** run native Windows applications.  Windows can't...  Isn't that enough?

---

