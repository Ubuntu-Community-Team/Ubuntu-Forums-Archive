---
title: "Problems with graphics driver."
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by wehttamb on 2006-10-10
:confused: i have just installed ubuntu and i need to install drivers for my onboard intel 815 graphics. i have no idea how to do it and i need help. here is a link to the release notes for the driver. could someone please look at them and tell me how to install the driver.
[http://downloadmirror.intel.com/df-support/2702/ENG/release_linux.pdf]("http://downloadmirror.intel.com/df-support/2702/ENG/release_linux.pdf")
i have downloaded the driver from [http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=797&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21]("http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=797&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21")
an it is in an RPM package.

:confused: :confused: :confused: PLEASE HELP!!!:confused: :confused: :confused:

---

### Post by wehttamb on 2006-10-10
By the way i read the release notes but had no idea what they were talking about.

---

### Post by meng on 2006-10-10
I thought Ubuntu came with built-in support for onboard Intel cards. What's the state of your machine right now? Do you have no graphics?

---

### Post by wehttamb on 2006-10-10
it is an old P3 and it has graphics but i can not do anything that involves 3D Graphics, i could use it to play 3D Games in windows.

---

### Post by meng on 2006-10-10
According to the posts in this thread:
[http://ubuntuforums.org/showthread.php?t=162679](http://ubuntuforums.org/showthread.php?t=162679)
you should have 3D support for that video card if you run in 16-bit color.

---

### Post by bodhi.zazen on 2006-10-10
> **wehttamb said:**
> :confused: i have just installed ubuntu and i need to install drivers for my onboard intel 815 graphics. i have no idea how to do it and i need help. here is a link to the release notes for the driver. could someone please look at them and tell me how to install the driver.
[http://downloadmirror.intel.com/df-support/2702/ENG/release_linux.pdf]("http://downloadmirror.intel.com/df-support/2702/ENG/release_linux.pdf")
i have downloaded the driver from [http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=797&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21]("http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=797&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21")
an it is in an RPM package.

:confused: :confused: :confused: PLEASE HELP!!!:confused: :confused: :confused:

Try this:```
sudo aptitude install 915resolution
```

If that does not work you can install the newest 1810 driver.

See here for gudence:[[color=navy]bodhi's Reesolution solution[/color]](http://ubuntuforums.org/showthread.php?t=269052)

---

