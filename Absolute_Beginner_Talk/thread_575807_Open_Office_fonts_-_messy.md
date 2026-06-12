---
title: "Open Office fonts - messy"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by jannen on 2007-10-14
Im running Ubuntu 7.04. Open office is now version 2.2. 

The fonts look very messy/scruffy in the Writer. Its hard to read documents, no matter which font style/size Im using. Other programs like Firefox and other text editors produce much clerar fonts. 

What should I do, what could be the problem?

---

### Post by bobplano on 2007-10-14
have you installed msttcorefonts? OOo uses open source fonts so they look different from fonts most people are used to. websites use web safe fonts and text editors use a different font.

---

### Post by jannen on 2007-10-15
Thanks.

How do I install msttcorefonts... please? Im a beginner!!!!

---

### Post by darren1270 on 2007-10-15
You can install the MS core fonts by installing the msttcorefonts package. To do this, enable the “Universe” component of the repositories. This is done by default in Feisty. After you do that, use the following command from the command line:

$sudo apt-get install msttcorefonts

You can find this here [http://ubuntu.wordpress.com/2005/09/09/installing-microsoft-fonts/](http://ubuntu.wordpress.com/2005/09/09/installing-microsoft-fonts/)


Good Luck 

Darren

---

