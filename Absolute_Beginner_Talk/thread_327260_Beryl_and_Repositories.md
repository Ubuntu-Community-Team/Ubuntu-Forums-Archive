---
title: "Beryl and Repositories"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by Blue_Sky on 2006-12-28
I have been trying to install Beryl, following [https://help.ubuntu.com/community/CompositeManager/InstallingBeryl](https://help.ubuntu.com/community/CompositeManager/InstallingBeryl), but the step that includes the code "deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main-edgy" and "wget [http://ubuntu.beryl-project.org/quinn.key.asc](http://ubuntu.beryl-project.org/quinn.key.asc) -O - | sudo apt-key add -" have stumped me. So far I have figured that the first line of code is not for the terminal, as it does not recognize "deb" as a valid command. For the second line I seem to be missing whatever a gpg key is and something else. Are there any other tutorials that explain this in plain English, or does anyone have the patience to explain any of my problems to me?

---

### Post by DaBigEd on 2006-12-28
You need to add these "deb" lines to your sources.list file. Details on doing this can be found at [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

