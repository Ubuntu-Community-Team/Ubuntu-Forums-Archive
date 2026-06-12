---
title: "Keyring problems"
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by Olderone on 2006-04-15
I have been recently trying to install real player in order to listen to BBC stored programmes.  On accessing root I am asked for the keyring password which is a puzzle as to my knowledge I have never supplied one. The root password and user account passwords are refused so I am baffled. Am I that senile that I have forgotten entering one? ( I confess that remembering the various passwords that I use is a problem at times) If this is the case is there a way of recovering /replacing the keyring password?
                      Hope someout there can help
Rich

---

### Post by ronmarley1 on 2006-04-15
Hi Rich,
Follow this to delete the keyring password and set another one.
Click on Places, Home Folder.  You will then need to hit Control+H on your keyboard to view hidden files.  (By the way, if you want to always view hidden files, you can click on Edit, Preferences and click the box in front of Show hidden and _b_ackup files.)  Browse to the folder called .gnome2, and then to the folder called keyrings.  Inside it is a file called default.keyring.  Delete it and the next time you enter a site or mount with a password, it'll ask for a keyring password, if you want to set one.

---

