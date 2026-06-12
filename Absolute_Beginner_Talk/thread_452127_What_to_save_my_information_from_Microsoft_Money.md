---
title: "What to save my information from Microsoft Money"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by michael_besselman on 2007-05-23
I am trying to completely switch from windows and everything is going fine thus far.  :D  I am looking to convert the data from my Microsoft Money 2006 file into an application on Linux.  I have installed and tried both Kmymoney and gnuCash.  I have seen some indication that they can indeed import my money file, but it does not work directly.  Is there a way to just import the data?  Is there a way to make Money output a file that can be imported into either of these two applications?  Is there an external file converter that will do the conversion for me?  I am tempted to write a converter if one does not exist, but am currently unsure of the formats of either file type and am not akin to reinventing the wheel if it already exists. ](*,)

Thanks

Michael Besselman

---

### Post by Iokua on 2007-05-23
In general, Microsoft does not make it easy to export data from their software into other applications. This is done to keep you from switching software. I'm not familiar with Microsoft Money though so I can't be sure that this is the situation.

If GnuCash has the ability to import, what do you mean that "it doesn't work directly?" How are you trying to import the file?

---

### Post by lazyart on 2007-05-23
According to the [website]("http://www.gnucash.org/"):> Playing With Others

As with other leading GNU/Linux software that is designed to replace proprietory programs, GnuCash is a functional replacement for expensive accounting programs. Like OpenOffice.org and The Gimp, GnuCash is also programmed to communicate and interact with as many existing programs, institutions and people as possible.

The GnuCash development team has continued to improve file import filters, which allow users to import work from old programs like Microsoft Money and Quicken. GnuCash can load QIF and QFX files, which are used by both of those programs.


Just a note... if you are using the version in the repositories you won't be able to use OFX, which connects directly to your bank and downloads updates.  You'll have to compile your own version if that's what you want.  I've done it, it's long an semi-painstaking, but it's a feature I thought that I must have.

---

### Post by MountainX on 2008-04-07
As far as I can tell, MS Money does not provide a way to export all financial data at once. It does allow export one account at a time. That makes the export process (and the subsequent import process) painstakingly slow and tedious.

If there is another way to get MS Money data into the QIF format, GnuCash and MoneyDance (and others) will be able to import it.

---

