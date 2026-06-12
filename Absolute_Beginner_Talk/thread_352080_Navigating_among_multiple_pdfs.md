---
title: "Navigating among multiple pdfs"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by bbukh on 2007-02-02
My configuration: Kubuntu 6.0.6 Dapper

I often have up to a dozen open pdf files. When there are more than three-four files open the navigation between them becomes extremely painful. The main reason is that each copy of kpdf creates a separate window, which shows in the taskbar. With more than handful windows, several copies of kpdf collapse into a single button on the taskbar saying "file://home/..." I have to click on that button and then read to the end of the URL to find the right file. I am eager to find a solution to this. The following is what I would like to do in the order from most preferrable to the least preferrable:

1) Have tabs in kpdf (ideally, two layers of them since one layer might not be enough)
2) Have some kind of program that can act as an better taskbar.
3) I tried to use firefox as "taskbar", but the problem that upon typing "firefox filename.pdf" the pdf is opened in a new tab in my main firefox window, which is itself cluttered with tabs. Adding 10 pdfs tabs to the existing 20 html tabs makes the tabs completely impossible to use. Any suggestion on how to deal with this is welcome.
4) Somehow merge the fix to the kpdf bug [http://bugs.kde.org/show_bug.cgi?id=103362](http://bugs.kde.org/show_bug.cgi?id=103362)  into dapper.
5) Anything else to ease the pain

Note that as for (4) manually upgrading to Kde 3.5.6 is not an option I even consider since it will break the security updates. However, I will consider switching to a different pdf viewer if that will help.

Thanks in advance.
--Boris

---

### Post by Paerez on 2007-02-02
Make a whole bunch of Workspaces and distribute the pdfs across them by category?

p.s. what are you working on that requires that many?

---

### Post by kebes on 2007-02-02
> **bbukh said:**
> 1) Have tabs in kpdf (ideally, two layers of them since one layer might not be enough)

Use Konqueror, which can display PDFs in its tabs (via kpdf no doubt). I just tried it and it works pretty well. You can open up new tabs in Konqueror and then open up the PDFs there. You can even drag new PDFs to the area just beside current tabs, and a new tab will be created with that PDF inside.

Of course you can have mutliple Konquerors (and on multiple desktops), so that you can keep different documents organized thematically.

Hope that helps.

---

### Post by bbukh on 2007-02-02
I figured out how to make (3) work in a satisfactory way. The extension "Too many tabs", which can be found at [http://jomel.me.uk/software/firefox/toomanytabs/](http://jomel.me.uk/software/firefox/toomanytabs/), eases handling of multiple firefox tabs. If someone knows how to implement (1) or (2), I would still be grateful.

In reply to Paerez: The idea of waddling from one workspace to another in attempt to find the right one does not appeal to me. The problem is that I do not have a perfect memory to remember where each file is. If I had a perfect memory, I would remember which of the icons on the taskbar corresponds to which file. As to what I need many pdfs for, let me say that I am a mathematician, and it is not uncommon for me to be looking at several papers at a time.

---

### Post by bbukh on 2007-02-03
> **kebes said:**
> Use Konqueror, which can display PDFs in its tabs...
Thank you a lot! This is a perfect solution. The Konqueror tabs interface is good: the right mouse button allows to choose a tab by name. In order to prevent tabs from shrinking to the point I could not read the titles, I had to set a minimum tab width as described in [http://wiki.kdenews.org/tiki-index.php?page=Secret+Config+Settings](http://wiki.kdenews.org/tiki-index.php?page=Secret+Config+Settings) (i.e. by setting MinimumTabLength=9 in [General] in ~/.kde/share/config/konquerorrc).

---

