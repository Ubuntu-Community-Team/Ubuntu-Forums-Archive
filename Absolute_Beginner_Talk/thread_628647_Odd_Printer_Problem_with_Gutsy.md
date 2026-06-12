---
title: "Odd Printer Problem with Gutsy"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by sanford55 on 2007-12-01
Hi everyone.  I sort of got my  my Brother 5250DN printer to work with Gutsy, OpenPrinting says it works well,  but only sort of.  It prints from a number of programs, but not from the crucial Open Office Writer.  If I try to print from that program, or even to look at set up options from inside that program, Open Office freezes (turns a grey color and then goes non-responsive).  Maybe I set up the printer incorrectly, but it does work on other programs.  Here is what I did to set it up.  I already have the Brother printer working on a windows network.  But on one of my computers, I dual boot into Ubantu.  I figured I should be able to print from both windows and ubantu.  I am a Linux newbie and did not know for sure what I was doing so I did the obvious.  I just went to administrator, and chose printer.  Nothing I saw seemed to find my networked printer so I figured the easiest thing to do (rather than playing around with networking) was to hook my Brother printer up to my parallel port.  Yep, Ubantu found the printer, I the correct model, and it seemed to install nicely.  I printed a test page fine.  And I printed a pdf page fine, and a page from a few other things.  I thought all was good to go till I tried printing from Open Office.  Crash.  I rebooted my computer, restarted the printer, a number of times, and no change.  I have no idea what might have gone wrong. I suppose this could be an open office problem, or a printer problem.  Any help would be much appreciated.

---

### Post by jkzubu on 2007-12-01
There is a known problem with Open Office in the way it reacts to various themes.  It may not be a problem with your printer.  Try searching for "Open Office Crashes" in this forum.  The problem is with Open office and there is a bug report for this issue.  I do dot think the problem has anything to do with a dual boot.  I solved the Open Office Crashing problem by switching my theme back to the base Human.  Then, Open Office worked fine.  Read through this link because it might help you: [http://ubuntuforums.org/showthread.php?t=584088](http://ubuntuforums.org/showthread.php?t=584088)

---

### Post by sanford55 on 2007-12-01
Yes!  I had changed themes, and I changed back to the human theme and printing in open office seems to work fine now.  I have not gone on to try other programs.  I does seem strange that something like a theme could have that impact.  Thanks for your help.  Sanford

---

### Post by GerryH on 2007-12-01
I have a Brother 420CN and in my user space OpenOffice prints fine. On my wifes side it will always hang when told to print
I found the way oround that pain is to open Print Preview, and it will print from the preview just fine.

---

