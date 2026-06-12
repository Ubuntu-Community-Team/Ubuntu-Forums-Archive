---
title: "Activating cfv when you click on an SFV file"
date: 2005-08-15
forum: Absolute Beginner Talk
---

### Post by dabotsonline on 2005-08-15
I am trying to enable cfv to check the hashes of MP3s when I click on the relevant SFV file in the folder.  I created a new file extension for "sfv" in "File Associations" and, using "cfv" as the preferred application, used the following command:

cd $pwd && cfv

However, say that I have the file **Nick_Polydor_Mix.sfv** in the folder **/home/nick/music/mixes/Nick_Polydor_Mix/**, cfv will only search files in the home directory, rather than the directory from which the SFV was launched from.  What command do I need to use instead of **$pwd**?

Thanks, Nick

---

