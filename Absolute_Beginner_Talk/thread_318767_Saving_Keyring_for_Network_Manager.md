---
title: "Saving Keyring for Network Manager"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by PartisanEntity on 2006-12-14
When I first set up Network Manager I did not want to save my keyring, so now whenever I want to connect to a network I am asked for the keyring password.

I have changed my mind and would like to store the password so it doesnt keep asking me, how would I do this?

TIA.

---

### Post by PartisanEntity on 2006-12-15
bump

---

### Post by PartisanEntity on 2006-12-16
bumptybump...

---

### Post by ngch on 2006-12-16
Do you want to make network manager stop asking for password, or is it that u want to set a keyring password?

If you want to stop network manager from constantly nagging you for the keyring password, you're in luck. The following guide can help you; read the section "Avoiding password nagging"
[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

The recommendation is that you set the keyring password to be the same as ur login password, so that you're less likely to forget.

---

### Post by Pobega on 2006-12-20
I have the same problem, but I no matter what I do it keeps asking for the Keyring Password!

When I first connected to my wireless network I hit "Deny" hoping that it wouldn't want a password at all, but now everytime I connect I need to type in my router's WEP password!

Is there any way to change/reset the keyring password?

---

### Post by ngch on 2006-12-21
You can try deleting the keyring file with these instructions:

1. Open your Home folder
2. Click on "View" and then click on "Show hidden files" You will see all the hidden files and folders, which start with "."
3. Open ".gnome2", and then open the "keyrings" folder. There should be a file name "default.keyring"
4. This is the part where you want to play safe. Backup the "default.keyring" file to another location eg. Desktop. Then, delete the original file.
5. Restart the computer
6. If all goes well, the keyring will be reset. Network Manager may ask you to enter the WPA passphrase again, after which it will ask you to set a new keyring password. Set the keyring password to be the same as your login password to avoid confusion in the future.

I hope this helps. :)

---

