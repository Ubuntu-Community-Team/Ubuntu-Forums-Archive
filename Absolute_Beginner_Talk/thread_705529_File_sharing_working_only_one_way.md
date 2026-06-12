---
title: "File sharing working only one way"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by t.septekin on 2008-02-23
I have two laptops connected in a network: an hp pavilion running Feisty and a sony vaio running Gutsy.

Working at pavilion, I can read/write files and create/delete folders in the two shared folders of vaio (/media/sda8 and /home/user).

Working at vaio, I can see the shared folders of pavilion (/media/hda8 and /home/user) but when I click either I get "The folder contents could not be displayed" error, I do not even get the "Authentication Required" window; a second request gives the same result.

Windows network support (SMB) has been installed in both; the folders in pavilion have been marked as shared and listed as such in smb.conf. The two smb.conf files are identical, excepting of course the hard disk names. Both devices have been restarted over and over.

Can someone make any suggestions, please?

---

### Post by cboebel on 2008-02-23
Did you create an SMB user on both sides and assign a password? I had a similar problem and solved it creating an SMB user and password.

Check out smbpasswd

---

### Post by t.septekin on 2008-02-23
I certainly did. What is more, vaio never asks for aunthetication.

---

