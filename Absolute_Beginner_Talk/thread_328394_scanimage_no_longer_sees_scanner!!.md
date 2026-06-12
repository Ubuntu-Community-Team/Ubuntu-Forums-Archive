---
title: "scanimage no longer sees scanner!!"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by moshuptrail on 2006-12-30
I went to use my scanner today and it was gone!
Re-booting to windows I was able to use it, so I know the hardware is working.
The scanner is an HP Officejet V40 multi-function printer, connected by usb.

scanimage -L reports:
```
No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
```

Thinking that maybe it is due to some recent update, I started looking at software libraries. I think I've upgraded HPLIP to 1.6.12 from the hplip.sourceforge web site.  (but I can't find a way to verify that it's working)

Then I began to doubt libusb.  Thinking I would need a higher version, I installed 0.1.8 (according to the HPLIP requirements)

Nothing has changed.  scanimage still reports as above.  ](*,) 
I know the usb is working because I can plug a memory stick and it works.

So what gives?  Why can't scanimage (or any other program) seem to find the scanner?

---

### Post by Sef on 2006-12-30
> I think I've upgraded HPLIP to 1.6.12 from the hplip.sourceforge web site.

Could uninstall the upgrades and then install what you had before?

---

### Post by moshuptrail on 2006-12-30
I probably could, but it wasn't working before I upgraded HPLIP and libusb.  So I wouldn't expect that to help.  The problem is, I'm not sure what changed previously to make it stop seeing the scanner.  It's been a month or so since I used it last.

Do you have any knowledge of the process by which sane figures out that there's a scanner there??  I'm just hoping it's some config file that's been changed by a routine upgrade.  I mean, everything else seems to be working.  Printing works!

---

