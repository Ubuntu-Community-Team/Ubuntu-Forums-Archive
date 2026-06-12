---
title: "Package Help!!!!!!!!"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by Shane_linuxnewb on 2007-04-19
Hi, i want to install java ( you might have seen my earlier posts :lolflag: ) but i cannot. I have been directed to: [http://packages.ubuntu.com/](http://packages.ubuntu.com/) but im not sure where to go from there i found some llikely files but am not sure how to download them.
do i download the entire package?
do i download the individual file?

THanks,
Shane

p.s. is there a way to see all my posts or threads?

Thanks

---

### Post by Shane_linuxnewb on 2007-04-19
wow, sorry for the annoying flag thing!

---

### Post by Sef on 2007-04-19
The easy way to install java:  

> Feisty Fawn 7.04 Development Branch

    *

      Click Applications &#8594; Add/Remove. In the top right, change the setting to "All available applications". Then select Other in the left panel and then select the Ubuntu restricted extras package. Click OK.
    *

      To play most DVDs you'll need the libdvdcss2 package. This package is available using Medibuntu. This is a third party package, and not supported by Ubuntu.

Note: If DVD playback fails, and you've never played any DVD before on your system, you may need the regionset package to initially set the drives region.

    *

      Some external codecs may be needed in order to play certain proprietary formats such as Apple Quicktime or RealVideo. These external codecs are available in the third-party repository of Medibuntu.


That´s from [restricted formats]("https://help.ubuntu.com/community/RestrictedFormats").  If you have **Dapper** still, go to [**restricted formats**]("https://help.ubuntu.com/community/RestrictedFormats").

---

### Post by Panzor on 2007-04-19
I sort of answered this question in your previous thread, but I'll revise it here anyway.
[http://www.java.com/en/download/linux_manual.jsp?locale=en&host=www.java.com](http://www.java.com/en/download/linux_manual.jsp?locale=en&host=www.java.com)
Download the "Linux(self-extracting file)." Not the RPM (that's for red hat)

cd to the directory that you saved that .bin file into.
Quick overview on CDing:
Run Terminal

```
 cd /[color=red]file location[/color]
```
example: cd /home/james/Desktop

Now,
```
 sudo sh [color=red]the name of the file[/color]
```
It should ask you to agree to terms, do that.
Tip: for the file name, you can aways use the tab-shortcut (type the first couple letters that distinguish it from other files and then press TAB).

I tried not to assume anything :).

---

### Post by Shane_linuxnewb on 2007-04-19
Thanks to both of you (especially for not assuming =]) ill get to work now and see if i can try to install it.

And is it possible to install AIM?

---

