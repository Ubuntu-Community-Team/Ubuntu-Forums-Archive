---
title: "Printing to high on page."
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by Klausbo on 2007-03-27
I have installed a cubs wrapper to make my brother DCP110C work in Ubuntu 6.06. I can now print, but the print is to high on the page, The problems occurs in all applications.
Another probems is that I enter greyscale in settings, the print comes out in colour.

hope for some usful information
Klaus

---

### Post by Scunizi on 2007-03-31
Open your browser and go to [http://localhost:631](http://localhost:631).  That is the Cups web based interface.  Make sure the settings for your printer match what you want.  I had to change my default printer paper size from A4 to Letter to make it print right. As for switching from color to grayscale, you're driver may not pass the information correctly to Cups.  So if you don't print grayscale too often you might consider using the link above on the odd occation that you need to make the change.

---

