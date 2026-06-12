---
title: "usb freezes my computer"
date: 2006-01-20
forum: Absolute Beginner Talk
---

### Post by ajosifoski on 2006-01-20
Ok ok I know that this is old problem and yesterday spent couple of hourse to find and did'nt succed.
So, when I plug usb stick system freezes.
When I turn usb printer system freezes.
Is there link step by step instructions about this problem?

---

### Post by Mustard on 2006-01-20
I just did a search on the forums for people who have may have had similar problems and my first advice would be to check your bios settings with relation to USB settings.  I don't know of any 'step by step' instructions for this problem unfortunately.  This might be a more a trial and error troubleshooting process.

Can you describe your system specifications to please?

---

### Post by ajosifoski on 2006-01-20
[QUOTE=Mustard]
Can you describe your system specifications to please?[/QUOTE]
MB MSI sis 645 Combo
VGA GeForce4 MX440/64/MB TV out
HDD 40GB Maxtor 7200 rpm
cpu 2GHz/128kb celeron
CDRW x48x16 sony

Printer Epson Stylus C43UX (want suggestions about)
:confused:

---

### Post by fiver on 2006-01-20
I have teh same problem, but with my new web camera. Whenever I fire up gnomemeeting (ie. when I actually start asking it to use  the usb device) it freezes rather completely.
Oddly, I do not know why only the camera, as I have used a usb mp3 player all right. So maybe it isn't the same thing?

---

### Post by ajosifoski on 2006-01-20
Problem was in BIOS setting
"**usb legacy mode**" was enable
would be **[COLOR="Red"]disable[/COLOR]**

---

### Post by Mustard on 2006-01-20
[QUOTE=ajosifoski]Problem was in BIOS setting
"**usb legacy mode**" was enable
would be **[COLOR="Red"]disable[/COLOR]**[/QUOTE]
Ah..excellent.  I read your post on your specs last night, but didn't see any comment on the checking the BIOS settings, so I wasn't sure whether you had to got around to doing that yet.  So has the problem dissappeared completely now?  I'd like to know how confident I can be in recommending this direction in troubleshooting in the future, as I have seen quite a number of posts on 'USB' and 'freezing' after doing that search earlier. :)

---

### Post by ajosifoski on 2006-01-21
[QUOTE=Mustard]Ah..excellent.  I read your post on your specs last night, but didn't see any comment on the checking the BIOS settings, so I wasn't sure whether you had to got around to doing that yet.  So has the problem dissappeared completely now?  I'd like to know how confident I can be in recommending this direction in troubleshooting in the future, as I have seen quite a number of posts on 'USB' and 'freezing' after doing that search earlier. :)[/QUOTE]

Well I must format ubuntu partition and install again to test it. That is because I find way to change _hcd (ehci first then ohci)
ohci is for usb 1.0
ehci is for usb 2.0
Steps (8) and (10) from here [http://www.ubuntuforums.org/showthread.php?t=80811](http://www.ubuntuforums.org/showthread.php?t=80811)
helped me also. But still I hope that only changing usb legacy to disable in bios will solve the problem

---

