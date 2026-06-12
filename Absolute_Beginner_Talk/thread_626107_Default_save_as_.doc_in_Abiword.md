---
title: "Default save as .doc in Abiword?"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by dmber on 2007-11-28
is there a way i can make it so that my default file format is .doc in abiword?

thanks.

---

### Post by mike555 on 2007-11-28
There are some properties of AbiWord that can be set in the preferences, but which do not yet have an entry in the Preferences dialog. To set these, you have to edit the preferences file by hand. On Linux and similar systems, this file is in the .AbiSuite folder in your home directory. This is a hidden directory; you will need to set your file manager to show such directories, or type the name by hand.

The file is called AbiWord.Profile, and you should open it in a text editor, not in AbiWord. When you do, you will notice that the comment information at the beginning of the file tells you not to edit the file by hand. If AbiWord came with any warranty, doing so would void the warranty. As it doesn't, you should simply make sure you save a copy of your preferences file before changing anything. Then, if everything goes wrong, you can replace the broken copy with the saved copy.

Most of the relevant options are in the Scheme sections. The first Scheme is the built-in scheme. It has name="_builtin_" as its first value. Do not bother editing this scheme, as it is reset whenever the application starts up. It provides default values, so that you only need to alter things when you want something different.

Your preferences are in the second scheme, with name="_custom_" as its first value. You should add lines to this scheme to set the additional preferences.

Useful values include:

DefaultSaveFormat=".abw" (Replace .abw with the suffix for any other file type to save as that file type by default.)(such as  .rtf )   (BE SURE TO PUT THIS BEFORE THE   /<   )

---

