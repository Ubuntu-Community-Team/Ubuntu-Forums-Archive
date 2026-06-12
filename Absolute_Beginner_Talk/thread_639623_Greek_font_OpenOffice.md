---
title: "Greek font OpenOffice"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by HaemoLacria on 2007-12-13
Can I use a greek font in OpenOffice [Ubuntu] ?

---

### Post by ^rooker on 2007-12-13
I haven't personally done it, but these 2 things might help you:

1) Open your favorite package manager (synaptic, aptitude, etc...) and search for "openoffice greek" - I'm running Dapper and "**apt-cache search openoffice greek**" it returns these packages:

> language-support-el - metapackage for Greek, Modern language support
myspell-el-gr - Greek (el_GR) dictionary for myspell
openoffice.org-l10n-el - Greek language package for OpenOffice.org
language-pack-el-base - translations for language Greek, Modern (1453-)

I recommend installing them all, and either the GNOME (Ubuntu) or KDE (Kubuntu) base package:
> language-pack-gnome-el-base - GNOME translations for language Greek, Modern (1453-)
language-pack-kde-el-base - KDE translations for language Greek, Modern (1453-)


2) Your question already seems to be successfully answered here:
[https://answers.launchpad.net/ubuntu/+source/openoffice.org/+question/12254](https://answers.launchpad.net/ubuntu/+source/openoffice.org/+question/12254)


Good luck!

---

### Post by Papa-san on 2007-12-13
Any ideas on how to install ancient greek?  I have the fonts, just not any knowledge as to how to install them and configure the keyboard...

---

### Post by thelatinist on 2007-12-13
> **Papa-san said:**
> Any ideas on how to install ancient greek?  I have the fonts, just not any knowledge as to how to install them and configure the keyboard...

I do ancient Greek in OpenOffice using Thessalonica for OpenOffice.org, which you can get from [http://www.thessalonica.org.ru/en/](http://www.thessalonica.org.ru/en/).  It allows you to type using deadkeys.

To install your fonts, copy them to /usr/share/fonts/truetype/myfonts.  Please note that OpenType fonts (.otf or .ttf with OpenType instructions) will not work in OpenOffice,org as of 2.3.  This is a problem with OpenOffice, not with Linux.

If you are interested, I have a custom keyboard layout for Thessalonica which I find more intuitive, and I also have an extensive list of autocorrect entries for OpenOffice which will speed up typing by accenting articles, pronouns, conjunctions, etc. for you.

---

### Post by euthyfro on 2008-03-10
How do i install Thessalonica now that i've downloaded the .zip?

---

### Post by euthyfro on 2008-03-10
nevermind i'm a idiot

---

### Post by simosx on 2008-03-16
If you want to add Greek support in Ubuntu, click on System/Administration/Language support. Then tick Greek and click Apply. The system will install the necessary packages. Please do not just install package names you read off the Internet as it will probably mess up your system.

To write Greek Polytonic in OpenOffice, you do not require the Greek support (from Language Support). 

Ubuntu comes already with two Greek Polytonic fonts, DejaVu Sans (also known as Sans) and MgOpen Canonica. It is not necessary to install more fonts, though they are easily available with the package manager.

To type Greek Polytonic, you can enable the Greek Polytonic keyboard layout (from Settings).

There is a bug in GTK+, and all versions of Ubuntu up to and including Ubuntu 8.04 will not write Greek Polytonic by default (am referring to the accents no being accepted). This will be fixed in Ubuntu 8.10, or, if you are adventurous enough, you can follow the instructions now,
[http://simos.info/blog/archives/661](http://simos.info/blog/archives/661)

An other alternative (if you do not want to wait for 8.10) is to edit /etc/environment and add the line 

GTK_IM_MODULE=xim

Restart your system, and then by using the Greek Polytonic keyboard layout you should be able to write Greek Polytonic.

---

### Post by andrew.46 on 2008-05-29
Hi:

> **thelatinist said:**
> If you are interested, I have a custom keyboard layout for Thessalonica which I find more intuitive, and I also have an extensive list of autocorrect entries for OpenOffice which will speed up typing by accenting articles, pronouns, conjunctions, etc. for you.

As a student of Ancient Greek I would be very interested in this,

        Andrew

---

### Post by Ludwig9 on 2008-05-30
> **andrew.46 said:**
> hi:



As A Student Of Ancient Greek I Would Be Very Interested In This,

        Andrew
&#924;&#949; &#964;&#959;&#959;.

---

### Post by Ludwig9 on 2008-05-30
> **simosx said:**
> An other alternative (if you do not want to wait for 8.10) is to edit /etc/environment and add the line 

GTK_IM_MODULE=xim

Restart your system, and then by using the Greek Polytonic keyboard layout you should be able to write Greek Polytonic.

Would please explain where and how to "edit /etc/environment"? Terminal? Synaptic? Do you mean to say that if the line GTK_IM_MODULE=xim is added one will be able to type Ancient Polytonic Greek (with all its accents, breathing marks, etc.) or just modern Greek with its few accents? 
I have already gone ahead and installed the Greek polytonic keyboard that is available in 8.04, and it allows me to type the acute accent over vowels:  &#940;&#941;&#943;&#973;, but no more. Will 8.10 provide a keyboard for ancient Greek with all its accents, breathing marks, iota subscript, etc.?  

Also, when is 8.10 supposed to come out? I am a newbie and Simos Xenitellis's commands are too adventurous for me. 
I have already encountered a problem with 8.04: the maximum number of keyboard layouts which can be installed at any one time is four. Cf. [http://ubuntuforums.org/showthread.php?t=810556](http://ubuntuforums.org/showthread.php?t=810556)

Why so few? Is there any chance that this number will be increased in the future?

---

### Post by simosx on 2008-06-20
> **Ludwig9 said:**
> Would please explain where and how to "edit /etc/environment"? Terminal? Synaptic? Do you mean to say that if the line GTK_IM_MODULE=xim is added one will be able to type Ancient Polytonic Greek (with all its accents, breathing marks, etc.) or just modern Greek with its few accents?

I have updated the blog post with more instructions. You use the terminal to type these commands. If you have any remaining questions, feel free to ask.

If you add that line, then Polytonic Greek works. Modern Greek works out of the box.

When you get Polytonic Greek to work with the instructions above, you can type things like &#940;&#8048;&#8118;&#8115;&#8065;&#8066;&#8069;&#8115;&#8118;&#8113;&#8112;&#912;.

> **Ludwig9 said:**
> I have already gone ahead and installed the Greek polytonic keyboard that is available in 8.04, and it allows me to type the acute accent over vowels:  &#940;&#941;&#943;&#973;, but no more.

The reason is that an important package is not updated in Ubuntu 8.04, and the easiest workaround for now is to add that special line in /etc/environment. There are other solutions as well, but they are far more advanced. Actually, if anyone is interested for the advanced solutions, I am happy to talk about (please).

> **Ludwig9 said:**
> Will 8.10 provide a keyboard for ancient Greek with all its accents, breathing marks, iota subscript, etc.?

Yes.

> **Ludwig9 said:**
> Also, when is 8.10 supposed to come out? I am a newbie and Simos Xenitellis's commands are too adventurous for me. 
I have already encountered a problem with 8.04: the maximum number of keyboard layouts which can be installed at any one time is four. Cf. [http://ubuntuforums.org/showthread.php?t=810556](http://ubuntuforums.org/showthread.php?t=810556)

Why so few? Is there any chance that this number will be increased in the future?

There is work going on to update the keyboard infrastructure in the Xorg server. Sadly, there is no funding for such work so it goes slowly. It is really sad, because the beneficiaries are so many that it would end up costing each one very little money.

---

### Post by Ludwig9 on 2008-06-20
simosx, I typed in Terminal: edit /etc/environment
and got the following result.  

george@george-desktop:~$ edit /etc/environment
Warning: unknown mime-type for "/etc/environment" -- using "application/*"
Error: no write permission for file "/etc/environment"
george@george-desktop:~$

---

### Post by simosx on 2008-06-20
The page does not mention a command "edit /etc/environment".

The commands are

sudo cp /etc/environment /etc/environment.ORIGINAL

and 

sudo gedit /etc/environment

---

### Post by Ludwig9 on 2008-06-20
sinosx, I wrote the commands in Terminal as instructed and got this result 

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games" 
LANGUAGE="en_US:en" 
LANG="en_US.UTF-8" 
GTK_IM_MODULE=xim

and saved it; restarted the computer, but it does not work properly. It gives me a grave accent, an acute, a circumflex and an iota subscript, but that's it. There are no breathing marks or breathing marks plus accents, and no way to make accents precede uppercase letters. Furthermore, use of the accents sometimes changes the size of the letters. Any suggestions?

---

### Post by simosx on 2008-06-21
Have a look again at
[http://simos.info/blog/archives/639](http://simos.info/blog/archives/639)

I added a newer update that you can try.

---

### Post by Ludwig9 on 2008-06-21
I haven't had a chance to test it out completely, but it looks like it works!:popcorn: Thanks!

&#8048;&#940;&#8118;&#8119;&#7939;&#7940;&#7943;&#7942;&#8071;&#8070;&#8081;&#7974; &#7951;&#7949;&#7948;&#7951;&#7950;

I have one other question now (and may well have others later): what fonts, sinosx, work best with  Greek? and what is the relation between the Greek fonts available in synaptic with the polytonic Greek keyboard layout? I have activated several of those fonts but they do not appear in the list of fonts when I write in Open Office.

---

### Post by simosx on 2008-06-21
> **Ludwig9 said:**
> I haven't had a chance to test it out completely, but it looks like it works!:popcorn: Thanks!

&#8048;&#940;&#8118;&#8119;&#7939;&#7940;&#7943;&#7942;&#8071;&#8070;&#8081;&#7974; &#7951;&#7949;&#7948;&#7951;&#7950;

I have one other question now (and may well have others later): what fonts, sinosx, work best with  Greek? and what is the relation between the Greek fonts available in synaptic with the polytonic Greek keyboard layout? I have activated several of those fonts but they do not appear in the list of fonts when I write in Open Office.

(dude, it's "simosx")

Sadly, OpenOffice.org does not support OpenType fonts yet. As far as I know, version 3.0, which comes in a few months will support OpenType fonts in Linux (in Windows, OpenType fonts can be used). Therefore, OOo cannot see your OpenType fonts in Linux yet.

I tend to use the default fonts in Ubuntu (Sans, which currently means DejaVu Sans). This is a TrueType font and works really well. Another option is to use Gentium.

---

