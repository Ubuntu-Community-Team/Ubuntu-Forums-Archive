---
title: "how to fill out PDF forms and actually SAVE your work?"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by uxohus2b on 2006-07-03
Hi,

Is there a program I can use to fill out PDF files with form entries (text, check boxes, etc) and save them? I understand that this is possible in acroread if and only if the person who made the PDF allowed form entries to be saved. Suppose they didn't. Is there a program for entering and saving form entries (I don't mean editing or creating PDFs). Solution to this problem would save me a lot of time and trouble. Thanks. h.y.

---

### Post by Jagot on 2006-07-03
I believe pdftk, which is in the universe repo, can do this.

---

### Post by indytim on 2006-07-03
Or, you might be able to fill it in as an OpenOffice doc and save it to pdf.

Just a thought...

IndyTim

---

### Post by xtacocorex on 2006-07-03
Adobe has a version of Acrobat 7.0 Reader for Linux. 

I think it can do forms. I'm not at home, so I can't check right now though.

---

### Post by aysiu on 2006-07-03
[QUOTE=indytim]Or, you might be able to fill it in as an OpenOffice doc and save it to pdf.

Just a thought...

IndyTim[/QUOTE]
I don't think OpenOffice can import PDFs.

You would need to use AbiWord or KWord.

---

### Post by uxohus2b on 2006-07-03
I installed pdftk, but I think it's mainly for managing PDF files in the terminal. There's no GUI. How do you use pdftk to fill out forms? 

Yes, I have acroread (Adobe Reader), but it doesn't allow you to save form entries, unless the person who created the original PDF went out of his way to allow it. 

I'm still lost. Any more suggestions? Thanks.

---

### Post by aysiu on 2006-07-03
You tried *kword*, too?

---

### Post by uxohus2b on 2006-07-03
Yup, I just installed and tried both Abiword and Kword. Both convert PDF files into plain text files. I don't see how a word processor can do what I want, but am I doing something majorly wrong here? I imported correctly, I'm sure. 

Here's a typical PDF file I would like to work on and save (download at bottom of page):
[http://www.uscis.gov/graphics/formsfee/forms/g-325a.htm](http://www.uscis.gov/graphics/formsfee/forms/g-325a.htm)

---

### Post by aysiu on 2006-07-03
I hate to say it, but those forms are designed *not* to save the information.

Your best bet may be to just fill it in and then save screenshots of the resulting document and then combine the screenshots together.

---

### Post by chajuram on 2006-07-04
I know you can do it if you have acrobat professional (not just reader). but it is expensive and huge

Just a thought, will printing to a pdf file after you fill in the form work?

---

### Post by uxohus2b on 2006-07-04
Yeah, I have Adobe Pro for Windows, which lets me save forms, even the ones from the above link. I'm just new to Linux and trying really hard to stay away from Windows. So I was hoping there might be a Linux equivalent of Adobe Pro or something (in terms of working with forms), but I guess not. 

As for chajuram's question: where would I print the PDF from? Only Acrobat Reader will let me fill out the forms, and other linux PDF editing programs don't even seem to recognize forms. So there's no program from which I might create a PDF output with the form data.

I might just have to use Windows to use Adobe Pro when I need it. Sucks. But I'll keep an eye out for any further suggestions in this matter. Thanks.

---

### Post by wylfing on 2006-07-05
I am pretty sure there is nothing on Linux that can do what you're describing. Whenever you talk about "PDF," people think there are a lot of Linux programs that can handle it. That is technically true, but the problem is actually *FDF*, the form data that Acrobat uses to do things like markups and filled-in form fields. So far as I have been able to discern, nothing outside of Acrobat Pro handles FDF worth beans.

It is possible to do some FDF things in the Linux Acrobat Reader, but only if someone has manually enabled such things for that particular document using [a Windows version of] Acrobat Pro v7.0+.

So, sadly, Windows is required for this. There simply aren't any alternatives and it's extremely likely there never will be.

---

### Post by uxohus2b on 2006-07-06
Thanks wylfing. Yeah, I was beginning to reach the conclusion you made. But I think a lot of people would find a program that allows you to fill out forms and save extremely useful, even if FDF is particular to Acrobat. Certainly, if I had the programming skills to create such a program, I would do it. I guess there must be other reasons I'm not aware of. Anyway, thanks for your response.

---

### Post by wylfing on 2006-07-06
The funny thing is, if these capabilities can be switched on in the Reader for Linux, you'd think that a full version of Pro could be done as well. Word is that there is a "shadow cabal" of Linux afficionados in Adobe, and a growing corporate resentment of Microsoft (viz. MS recent moves to compete directly with Adobe), so hopefully we will see Pro for Linux emerge. I know that I would immediately purchase Pro for Linux if it existed.

---

### Post by joehill on 2006-09-08
I just had the same problem and did a search on Synaptic and came up with fplsed, which is a wysiwyg interface for adding text on top of .ps files, but it can import and export between .pdf so in effect you're editing a .pdf doc.  I just used it to fill out a form and it was fine.  The interface isn't as modern and fancy as some, but it does the job.  It doesn't actually treat it as a form though, just a pdf that you're laying text on top of, but you can position it well using arrow keys.

---

### Post by aysiu on 2006-09-08
Is that effect in *fplsed* any different from editing in KWord? Just curious.

---

### Post by dief-eh? on 2006-11-24
hello,
I have read this thread with interest, but remain confused. Is it possible to use openoffice, for example, to *fill-in* .pdf form documents? If so, how? When I open a four-page job application .pdf in openoffice, I get a 366-page document of apparent gibberish that makes .html documents seem paragons of perspicacity by comparison! What gives?

As always, any responses greatly appreciated.

---

### Post by aysiu on 2006-11-24
> **dief-eh? said:**
> hello,
I have read this thread with interest, but remain confused. Is it possible to use openoffice, for example, to *fill-in* .pdf form documents? If so, how? When I open a four-page job application .pdf in openoffice, I get a 366-page document of apparent gibberish that makes .html documents seem paragons of perspicacity by comparison! What gives?

As always, any responses greatly appreciated.
In answer to your question... no.

You cannot use OpenOffice to fill in a .pdf form.

You can use OpenOffice to create a PDF (and even that won't be a form).

You can, if the form is created *correctly*, use Adobe Reader (which exists for Linux) to fill in the form.

You can also, if the form is not created correctly, use KWord to import the PDF to an editable document, fill out the form, and export it again, but the formatting might be off a bit.

---

### Post by sadjack on 2006-11-24
If you want to save the document after filling it in, what hapens if you print and select "print to file", does it keep the completed fields and can you open the print file afterwards? I can't access the forms you linked to for some reason.

---

### Post by Jabran Asghar on 2007-11-30
Hello,

Just in case anyone is still looking for an application to edit/save PDF Forms ... use CABAReT:

[http://www.cabaret-solutions.com/en]("http://www.cabaret-solutions.com/en")

It is free for personal use and seems to do the job very well :-)

Jabran

---

### Post by hanzj on 2008-03-10
Jabran,
will look into Cabaret.


---

### Post by mowgliee on 2008-06-04
oddly enough i just discovered and tested cabaretstage yesterday, BEFORE reading this thread.  irony!  it does work.  i edited a pdf which i made using scribus and saved the data for edit later!

muy bueno!

but what i'm looking for is how to use openoffice to create that pdf fill in form instead of scribus.  scribus doesnt have all the editing & formating features of writer.

someone earlier said if you do it right, you can make a pdf form which others can use adobe reader to fill in (though not save).  thats exactly what i want!!!  but how?

---

### Post by maria@pdffiller on 2008-06-29
You can try [www.pdffiller.com](www.pdffiller.com) to fill in your pdf forms. It is probably the easiest way to do that. You don`t have to install any software. Just click anywhere and start typing. You can print, Email, fax, or export your form as well.

---

### Post by CRCarl on 2008-06-30
I have used Cabaret, that works, but most of the time I just use Gimp. Save as a .ps and used ps2pdf to convert it. Creates small files I can go back and edit later, just make sure you save as a regular Gimp file and a .ps export. 

Craig

---

### Post by Mary2day on 2008-07-09
What do you think about [www.PDFfiller.com?](www.PDFfiller.com?) It`s a nice web based pdf editor.Easy fast and doesn`t required any additional software installation. Will be happy to hear what you think about it.

---

### Post by hyper_ch on 2008-07-23
Hmmm Cabaret Solutions looks very interesting. I tried it on windows and it works great but can't get it to run on linux. With wine it won't work it. It starts the program but has problems with java (I did install the .exe with JRE for wine).

When I run it on Ubuntu Hardy 64bit with Sun Java 6 I get those errors:

Running cabaretstage binary:
```

hyper@xubi:~/Desktop/cabaretstage-3.2.7$ ./cabaretstage
Find JVM: trying $CABARET_JAVA_HOME
Find JVM: trying private jre
Find JVM: trying $JAVA_HOME
Find JVM: trying /etc/jvm entries
Find JVM: assuming jvm library will be found in $LD_LIBRARY_PATH
Found libjvm.so.
Cannot open libjvm.so
Cannot launch virtual machine.
hyper@xubi:~/Desktop/cabaretstage-3.2.7$ 

```

-----------------

Running the .sh file (as recommended for 64bit)
```

hyper@xubi:~/Desktop/cabaretstage-3.2.7$ ./cabaretstage.sh 
[23.7.2008-14:16:11:127  ][SEVERE   
][de.intarsys.graphic.freetype.Freetype][Freetype initializer] can't initialize
freetype
java.lang.UnsatisfiedLinkError:
/home/hpyer/Desktop/cabaretstage-3.2.7/bin/libfreetype_wrap.so:
/home/hyper/Desktop/cabaretstage-3.2.7/bin/libfreetype_wrap.so: wrong ELF class:
ELFCLASS32 (Possible cause: architecture word width mismatch)
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1767)
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1692)
        at java.lang.Runtime.loadLibrary0(Runtime.java:840)
        at java.lang.System.loadLibrary(System.java:1047)
        at de.intarsys.graphic.freetype.ftnative.freetypeJNI.<clinit>(Unknown Source)
        at de.intarsys.graphic.freetype.ftnative.FT_LibraryRec.<init>(Unknown Source)
        at de.intarsys.graphic.freetype.Freetype$Mode_Native.initFreeType(Unknown Source)
        at de.intarsys.graphic.freetype.Freetype.initFreeType(Unknown Source)
        at de.intarsys.pdf.rendering.freetype.FreetypeTextRenderer$1.run(Unknown Source)

[23.7.2008-14:16:13:82   ][SEVERE    ][de.intarsys.tools.reporter][main] can't start
IMain
java.lang.UnsatisfiedLinkError: no swt-gtk-3347 or swt-gtk in swt.library.path,
java.library.path or the jar file
        at org.eclipse.swt.internal.Library.loadLibrary(Library.java:219)
        at org.eclipse.swt.internal.Library.loadLibrary(Library.java:151)
        at org.eclipse.swt.internal.C.<clinit>(C.java:21)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
        at org.eclipse.swt.widgets.Display.<clinit>(Display.java:128)
        at com.cabaret.application.swt.SWTApplication.basicStart(Unknown Source)
        at com.cabaret.application.common.CommonApplication.start(Unknown Source)
        at com.cabaret.application.common.CommonApplication.start(Unknown Source)
        at com.cabaret.platform.stage.CommonStage.start(Unknown Source)
        at com.cabaret.platform.stage.StandardStage.main(Unknown Source)

```

--------------------------

Cating the jvm:
```

hyper@xubi:~/Desktop/cabaretstage-3.2.7$ cat /etc/jvm
# This file defines the default system JVM search order. Each
# JVM should list their JAVA_HOME compatible directory in this file.
# The default system JVM is the first one available from top to
# bottom.

/usr/lib/jvm/java-gcj
/usr/lib/jvm/ia32-java-1.5.0-sun
/usr/lib/jvm/java-1.5.0-sun
/usr
hyper@xubi:~/Desktop/cabaretstage-3.2.7$ 

```

I guess those java errors are the problem when running with the .sh script as recommended for 64bit. However that does not help me much.

---

