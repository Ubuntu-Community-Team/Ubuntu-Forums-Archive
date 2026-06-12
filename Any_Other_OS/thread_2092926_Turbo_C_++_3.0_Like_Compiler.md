---
title: "Turbo C ++ 3.0 Like Compiler"
date: 2012-12-09
forum: Any Other OS
---

### Post by ramakanta on 2012-12-09
Is any compiler(best) ( whole IDE )available as Turbo C++ 3.0 which can run in windows 7. please help me.
Thank you.

---

### Post by TheFu on 2012-12-09
> **ramakanta said:**
> Is any compiler(best) ( whole IDE )available as Turbo C++ 3.0 which can run in windows 7. please help me.
Thank you.

**Microsoft Visual Studio**, MSVS, has taken almost the entire C++ market for Windows C++ development, at least for professional coders.

You can setup a UNIX-like environment using command line tools for debugging and compiling with IDEs like **Geany** or a bloated Java-based **Eclipse**. There must be other similar IDEs, but each will need lots of manual setup - they are not all-in-one like MSVS or Turbo C++ was.

Microsoft used to release a free command line version of their Windows C++ compiler. I don't recall the details, but there was some hub-bub about a change in license/distribution a few months ago before the Win8 release.

I miss TurboC++ - it was a simple, efficient tool for building small projects.  I probably still have a few licenses here along with Borland C++ and C++-builder licenses.

Since this is a Linux-centric forum, I'd encourage you to learn to program for Linux systems using Geany, ddd/gdb, g++ compiler, and Makefiles.  This knowledge will transfer to almost every other platform, though it is not an all-in-one solution.

Geany is a cross-platform editor like Notepad++, if you haven't converted to vim or emacs yet. Any editor can be used for Linux development. ddd is a good C++ debugger GUI into gdb.  gmake is a project build scripting language and tool that can make building the different parts of a program easy. The Makefile descriptive language is a little different - it depends on tabs, so be cautious with any editor that changes spaces and tabs automatically.

Out of curiosity, I asked AlternativeTo.net for an alternative to TurboC++ - [http://alternativeto.net/SearchResult.aspx?search=turbo+c%2B%2B](http://alternativeto.net/SearchResult.aspx?search=turbo+c%2B%2B) some interesting results there.

---

