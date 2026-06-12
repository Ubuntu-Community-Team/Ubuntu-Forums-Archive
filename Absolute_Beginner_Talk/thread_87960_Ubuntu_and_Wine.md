---
title: "Ubuntu and Wine"
date: 2005-11-09
forum: Absolute Beginner Talk
---

### Post by Stormspace on 2005-11-09
I installed Wine several times with mixed results, but finnally found an option in the file view options where I could expose hidden and system files. Once there I noticed that all of the wine installations had created it's own set of directories. I deleted all of these and installed wine again.

The first app I installed was the AD&D Core Rules 2.0 and the installation went very quickly, unlike in previous attempts when it was dog slow during the install. I can only assume that the multiple fake windows directories was the culprit. At any rate, once the app was installed I was able to run it with out any problems, but my question is; If I hadn't enabled viewing of hidden files I would never have been able to execute the app, so is something hosed on my Wine/Ubuntu install that's keeping me from seeing the installed apps?

---

### Post by Pablo_Escobar on 2005-11-09
No, the hidden part is perfectly normal. It's the configuration setup of Wine for a specific user.
the /home/username/.wine   directory is hidden by default, so as other configuration directories.

---

