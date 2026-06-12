---
title: "Mouse problem in new machine"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by Linux Lover on 2007-01-01
i have installed a new machine yesterday and installed ubuntu (dapper) there. it is also updated and upgraded. after the upgrade i am feeling a typical problem in mouse. it seemed that somebody is clicking the mouse repeatedly even then when there is no activity of mouse. it sometime scrolling down, sometime selecting the desktop, sometime opening the Application menu and starting opening an application repeatedly. when it starts these sort of malfunctioning i cannot control it and i have to press ctrl+alt+bkspace and then reboot.

even after reboot, it is not staying normal. say after half an hour or so, it starts malfunctioning such a way.

why it is happening so? please help,........ i am really fedup with the mouse problem.

regards
linux lover

ps : changing with another mouse could not solve the problem

---

### Post by bodzasfanta on 2007-01-04
Hello!

I had a similar problem but thanks God someone told me a good way to fix it.

"In grub, hit e to edit the boot line. Then move the selection over the kernel line and hit e again. Move the cursor to the end of the line and add the following:
Code:

noapic irqpoll pci=routeirq

Then hit enter to get our of line editing mode and b to boot the modified kernel line.

This will set you up until you power down or reboot. Edit /boot/grub/menu.list to make it permanent." (thanks for Frem)

I hope I could help you

---

