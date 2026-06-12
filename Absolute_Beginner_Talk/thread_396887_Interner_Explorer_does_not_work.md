---
title: "Interner Explorer does not work"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by hosammy on 2007-03-30
Hi, I have just installed the Internet explorer and have followed the instructions in [http://www.psychocats.net/ubuntu/ies4linux](http://www.psychocats.net/ubuntu/ies4linux) and [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Internet_Explorer_.2B_Flash_9_.28IEs4Linux.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Internet_Explorer_.2B_Flash_9_.28IEs4Linux.29)

When I try to execute the ie6. In the terminal I found the following response then halt.

[COLOR="Green"]fixme:actctx:ActivateActCtx 0xf00baa 0x33f53c
fixme:actctx:DeactivateActCtx 00000000 00f00bad
err:shell:ReadCabinetState Initializing shell cabinet settings
fixme:actctx:ActivateActCtx (nil) 0x33ed9c
fixme:actctx:CreateActCtxW 0x33d340 00000008
fixme:actctx:ActivateActCtx 0xf00baa 0x33d108
fixme:actctx:DeactivateActCtx 00000000 00f00bad
fixme:actctx:ActivateActCtx 0xf00baa 0x33dce8
fixme:actctx:DeactivateActCtx 00000000 00f00bad
err:rebar:REBAR_WindowProc unknown msg 200b wp=00000000 lp=71180f00
fixme:actctx:CreateActCtxW 0x33d1e4 00000008
fixme:actctx:ActivateActCtx 0xf00baa 0x33cfac
fixme:actctx:DeactivateActCtx 00000000 00f00bad
fixme:actctx:ActivateActCtx 0xf00baa 0x33dc40
fixme:toolbar:TOOLBAR_CheckStyle [0x10050] TBSTYLE_REGISTERDROP not implemented
fixme:toolbar:TOOLBAR_CheckStyle [0x10050] TBSTYLE_REGISTERDROP not implemented
fixme:actctx:DeactivateActCtx 00000000 00f00bad
fixme:shell:NTSHChangeNotifyRegister (0x10050,0x00008003,0x00008000,0x0000c07d,0x00000001,0x33dc50):semi stub.
fixme:toolbar:TOOLBAR_Unkwn45D hwnd=0x10050, wParam=0x00000000, size.cx=1024, size.cy=32000 stub!
fixme:toolbar:TOOLBAR_CheckStyle [0x10050] TBSTYLE_REGISTERDROP not implemented
fixme:toolbar:TOOLBAR_CheckStyle [0x10050] TBSTYLE_REGISTERDROP not implemented
[/COLOR]

Please advise ...

---

### Post by nixclusive on 2007-03-30
man why would you want to run IE on linux? anyways you can try upgrading wine..

---

### Post by freebird54 on 2007-03-30
Was wine working before you started?

---

### Post by hyper_ch on 2007-03-30
maybe he develops websites... that would be about the only reason to get msie installed...

---

### Post by Spr0k3t on 2007-03-30
> **hyper_ch said:**
> maybe he develops websites... that would be about the only reason to get msie installed...

As a web developer myself, I don't bother with IE.  It's a lot easier to develop for standards than it is trying to make a page look pretty for IE.

---

### Post by hyper_ch on 2007-03-30
That's good for you... but if 80% of your visitors use MSIE and the site looks shitty in MSIE then you have a problem...

Coding for standards is nice but creating commercial websites is about selling something to the customer...

---

### Post by hosammy on 2007-03-31
Reply to nixclusive:
[COLOR="DarkRed"]man why would you want to run IE on linux? anyways you can try upgrading wine..[/COLOR]
1. Some financial instutions' web sites only allow the MS IE to operate their internet banking. eg. [http://www.winglungbank.com/](http://www.winglungbank.com/)
2. I think I am using the latest wine 0.9.33 as I use the Synaptic Manager to install it.

Reply to freebird54:
[COLOR="DarkRed"]Was wine working before you started?[/COLOR]
I don't know since I only use wine to start the MS IE and my Ubuntu Egdy has been just installed.

:confused:

---

### Post by vnt87 on 2007-03-31
I use IE4Linux as well but did not run into such a problem. Have you tried the .deb package mentioned in this thread: [http://ubuntuforums.org/showthread.php?t=370705](http://ubuntuforums.org/showthread.php?t=370705)

---

### Post by hosammy on 2007-03-31
I tried to run it again and wait for more than half an hour, the outcome is slightly different now:
[COLOR="Red"]
fixme:actctx:CreateActCtxW 0x33fb10 00000008
fixme:actctx:ActivateActCtx 0xf00baa 0x33f8d8
fixme:actctx:DeactivateActCtx 00000000 00f00bad
err:ntdll:RtlpWaitForCriticalSection section 0x7ea715c0 "x11drv_main.c: X11DRV_CritSection" wait timed out in thread 000c, blocked by 000b, retrying (60 sec)
fixme:actctx:CreateActCtxW 0x33f774 00000008
err:shell:ReadCabinetState Initializing shell cabinet settings
fixme:actctx:CreateActCtxW 0x33d340 00000008
err:rebar:REBAR_WindowProc unknown msg 200b wp=00000000 lp=71180f00
fixme:actctx:CreateActCtxW 0x33d1e4 00000008
fixme:toolbar:TOOLBAR_CheckStyle [0x10034] TBSTYLE_REGISTERDROP not implemented
fixme:toolbar:TOOLBAR_CheckStyle [0x10034] TBSTYLE_REGISTERDROP not implemented
fixme:shell:NTSHChangeNotifyRegister (0x10034,0x00008003,0x00008000,0x0000c074,0x00000001,0x33dc50):semi stub.
fixme:toolbar:TOOLBAR_Unkwn45D hwnd=0x10034, wParam=0x00000000, size.cx=1024, size.cy=32000 stub!
fixme:toolbar:TOOLBAR_CheckStyle [0x10034] TBSTYLE_REGISTERDROP not implemented
fixme:toolbar:TOOLBAR_CheckStyle [0x10034] TBSTYLE_REGISTERDROP not implemented
wine: Critical section 7ea715c0 wait failed at address 0x7bc2f410 (thread 000c), starting debugger...
WineDbg starting on pid 000a
Unhandled exception: wait failed on critical section 0x7ea715c0 thread_data_tls_index+0x44
err:seh:raise_exception Unhandled exception code c0000194 flags 0 addr 0x7bc2f410
Process of pid=000a has terminated
Wine-dbg>
[/COLOR]

:confused:

---

### Post by david_kt on 2007-03-31
I saw you bank allow IE and Netscape. We have Netscape for linux:

[http://browser.netscape.com/ns8/download/archive72x.jsp](http://browser.netscape.com/ns8/download/archive72x.jsp)

I think to run Netscape is much easier then IE.

DK

---

### Post by brennydoogles on 2007-03-31
> **hosammy said:**
> Reply to nixclusive:
[COLOR="DarkRed"]man why would you want to run IE on linux? anyways you can try upgrading wine..[/COLOR]
1. Some financial instutions' web sites only allow the MS IE to operate their internet banking. eg. [http://www.winglungbank.com/](http://www.winglungbank.com/)
2. I think I am using the latest wine 0.9.33 as I use the Synaptic Manager to install it.

Reply to freebird54:
[COLOR="DarkRed"]Was wine working before you started?[/COLOR]
I don't know since I only use wine to start the MS IE and my Ubuntu Egdy has been just installed.

:confused:

Have you tried installing the IETab addon for firefox?? It would allow you to open your bank's webpage in the IE engine without having to install IE. You could also set it to always open that page in IE by default, to save you some trouble!! Just for future reference... if you hit the # before you enter in output of your terminal, you will wrap code tags around the text, which will prevent any smilies from sneaking their way into your code. Have a great day!!

---

### Post by vnt87 on 2007-03-31
I thought the IETab addon only work on Windows?

---

### Post by hosammy on 2007-04-01
Reply to brennydoogles:
[COLOR="DarkOliveGreen"]Have you tried installing the IETab addon for firefox?? It would allow you to open your bank's webpage in the IE engine without having to install IE. You could also set it to always open that page in IE by default, to save you some trouble!! Just for future reference... if you hit the # before you enter in output of your terminal, you will wrap code tags around the text, which will prevent any smilies from sneaking their way into your code. Have a great day!![/COLOR]

The IE Tab extension in firefox only supports Windows + IE >4.0, see Project info in [http://ietab.mozdev.org/](http://ietab.mozdev.org/)

Reply to vnt87:
I am trying to work in your suggestion now, wait and see...

:confused:

---

### Post by Spr0k3t on 2007-04-01
IETab requires the IE dll components to wrap the engine inside of the Firefox browser.

---

### Post by hosammy on 2007-04-01
I repeat the installation IES4LINUX for many time. The results are:
Ubuntu 6.10 Egdy system language is Chinese (TW), MSIE 6.0 language is English, not work.
Ubuntu 6.10 Egdy system language is Chinese (TW), MSIE 6.0 language is Chinese (TW), not work.
Ubuntu 6.10 Egdy system language is English (EN-US), MSIE 6.0 language is English, work.
Ubuntu 6.10 Egdy system language is English (EN-US), MSIE 6.0 language is Chinese (TW), it works but the fonts in MSIE cannot be displayed in order but with question marks only.

I think the problem is the IES4LINUX.
:confused:

---

