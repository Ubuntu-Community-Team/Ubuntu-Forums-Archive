---
title: "Remove beryl"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by kcirtap on 2007-07-06
I made the mistake to install to much desktop features like Beryl and now I want to remove it. I searched around a while and found the following command: 'sudo apt-get remove beryl emerald-themes', but i'm sure that doesn't remove it completely.

Is there any way to search for all installed files from the terminal and remove them one by one, or is there a command that will completely remove it from the hard drive?

---

### Post by Vajra Vrtti on 2007-07-06
Remove them with Synaptic marking them for **complete removal**.

---

### Post by Vajra Vrtti on 2007-07-06
If you want to see what files a package installs, use Synaptic *Settings -> Preferences*. In the *General* tab mark the first option, *Show package properties in the main window*. That will make that information available.

---

### Post by bigken on 2007-07-06
sudo aptitude remove beryl emerald-themes

---

### Post by Vajra Vrtti on 2007-07-06
After the complete removal, check if the hidden folders ~/.beryl and ~/.emerald were properly deleted.

---

