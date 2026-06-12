---
title: "Problem with installation..."
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by scythedxheartx on 2007-04-03
Just to let all of you know, I am a high school student just learning about computer talk and everything...so stuff like ACPI i won't understand

I have an old Windows 95 and I started deleting programs awhile ago, and i rebooted it...and then it wouldn't work without an activation disk. Then yesterday i learned about Lindux from the computer teacher in my school. He said that Lindux would make it reboot again so it'd work under lindux. So i have tryed and it has worked until it starts installing. 

I go to the main page and choose the option "Start or Install Unbuntu"

After that it starts up but then it comes to a page with the "ACPI: Unable to Locate RSDP" thing...

any ideas??

:popcorn: :guitar:

---

### Post by phr0z3n on 2007-04-03
My guess is it doesent support it, if its an old machine, and I assume it is if you are using Windows 95.

---

### Post by Daishiman on 2007-04-03
Ubuntu is not really the best performer for a windows95 era machine. You might want to look into Feather Linux or Damn Small Linux, which have lighter but less flashy graphical environments.

Otherwise in the boot options I'd try to boot with the option noacpi or acpi=off, and if any of those don't work, try adding noapic or nolapic.

---

