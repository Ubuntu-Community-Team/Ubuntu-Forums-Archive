---
title: "Installing seguibk.ttf"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by dannymichel on 2007-06-09
I downloaded seguibk.ttf font and I want to install it. Can someone help me out with that?

---

### Post by lawr_rawr on 2007-06-09
Open your home folder. If you don't have a location bar, click the notepad icon to see it.
Go to fonts:/// 
Then drag your new font into this folder. You might need to log out and in again before you can select the new font.

---

### Post by Funktown on 2007-06-09
Another method of installing fonts can be used from the terminal, and is much easier (in my opinion).

First, create the ~/.fonts directory if it doesnt exist
```
mkdir ~/.fonts
```

Then, copy your .ttf file into the directory we just made
```
cp seguibk.ttf ~/.fonts
```

Lastly, update your font-cache by issuing the following command:
```
fc-cache -f -v ~/.fonts 
```

Hopefully that helps! The last step *might* need to be run using sudo, but I don't believe it should be necessary.

---

