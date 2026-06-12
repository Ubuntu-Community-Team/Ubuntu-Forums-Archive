---
title: "Undo macbook backlight mod"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by erasmosis on 2007-10-06
AHH!

So I was just setting up ubuntu on my macbook, 
and I accidentally followed the instructions for pre feisty.... 

> wget [http://ubuntu.desrt.ca/macbook-backlight_0.0-1_i386.deb](http://ubuntu.desrt.ca/macbook-backlight_0.0-1_i386.deb)
gdebi-gtk macbook-backlight_0.0-1_i386.deb
sudo chmod u+s /usr/bin/macbook-backlight
gconftool-2 --type string --set /apps/metacity/global_keybindings/run_command_1 "0x65"
gconftool-2 --type string --set /apps/metacity/global_keybindings/run_command_2 "0xd4"
gconftool-2 --type string --set /apps/metacity/keybinding_commands/command_1 "/usr/bin/macbook-backlight -10"
gconftool-2 --type string --set /apps/metacity/keybinding_commands/command_2 "/usr/bin/macbook-backlight +10"

I uninstalled the backlight program, but im not sure how to return the fkeys back to the default.  
I'm really new to ubuntu, and I have no idea what to do...

I'd really appreciate any help you can give me...

---

