---
title: "Power management on a laptop..."
date: 2005-07-28
forum: Absolute Beginner Talk
---

### Post by [Cyanide] on 2005-07-28
Is there a place to configure it?

Whenever I shut the lid for my laptop it goes into sleep & eventually shuts down...

---

### Post by bearbigears on 2005-07-28
go to system > preferences > screensaver> advance tab. this should get you started



respect

---

### Post by [Cyanide] on 2005-07-28
[QUOTE=bearbigears]go to system > preferences > screensaver> advance tab. this should get you started

respect[/QUOTE]

You know I did that, but it still doesn't work :-?

---

### Post by bearbigears on 2005-07-28
now you have me wondering.

---

### Post by poofyhairguy on 2005-07-29
[QUOTE='[Cyanide]']Is there a place to configure it?

Whenever I shut the lid for my laptop it goes into sleep & eventually shuts down...[/QUOTE]

Suspend and hibernate are not stable features in Ubuntu yet.

[https://wiki.ubuntu.com/HoaryPM?highlight=%28pm%29](https://wiki.ubuntu.com/HoaryPM?highlight=%28pm%29)

Its kinda hard to control. Two releases till that is fixed for most I bet.

If you have an old laptop, use apm instead of ACPI. APM support is perfect for me. Since ACPI is a Microsoft feature (instead of an industry standard like APM) it will take a while for the Linux people to get it all figured out.

I hope that link and info can help you some.

---

### Post by [Cyanide] on 2005-07-29
[QUOTE=poofyhairguy]Suspend and hibernate are not stable features in Ubuntu yet.

[https://wiki.ubuntu.com/HoaryPM?highlight=%28pm%29](https://wiki.ubuntu.com/HoaryPM?highlight=%28pm%29)

Its kinda hard to control. Two releases till that is fixed for most I bet.

If you have an old laptop, use apm instead of ACPI. APM support is perfect for me. Since ACPI is a Microsoft feature (instead of an industry standard like APM) it will take a while for the Linux people to get it all figured out.

I hope that link and info can help you some.[/QUOTE]

Well actually I'd rather have the laptop NOT be put into suspend/hibernate when I shut the lid.

So if there's some way to disable that function while keeping the rest of the ACPI functions that'd be nice.

---

### Post by Kitty on 2005-07-29
See [http://ubuntuforums.org/showthread.php?t=29164&highlight=ACPI+lid](http://ubuntuforums.org/showthread.php?t=29164&highlight=ACPI+lid)

They talk about the scripts run when lib is closed.

---

