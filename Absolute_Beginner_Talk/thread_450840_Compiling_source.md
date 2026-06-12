---
title: "Compiling source"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by silentjudas on 2007-05-21
ok, i've looked this up everywhere. yes i have build-essential installed and all update
i can ./configure souce. errors (see lower on page)
what i cant do is make. make never works for me. it always says there is no make file no matter what!


whats up with that!??!?!

---

### Post by Hobo Joe on 2007-05-21
What are you trying to compile?

This happened to me once, but being a noob, I had never realized that it was already compiled and ready to go, and I just had to install a package to run it.

---

### Post by apjone on 2007-05-21
is this on everything or just one package?

---

### Post by taurus on 2007-05-21
Not everything that you download requires you to run ./configure && make && sudo make install.  Some of them are already a binary so you just execute the program directly from where you unpack it.

What are you trying to build anyway?

---

### Post by silentjudas on 2007-05-21
trying to build xmule, but this happens with everything i try and build.
and here, i'll show u a pic of the folder. i get an odd error compiling this one in partic that i dont think i saw on others. 
```

configure: error:
            Please check that wx-config is in path, the directory
            where wxWindows libraries are installed (returned by
            'wx-config --libs' command) is in LD_LIBRARY_PATH or
            equivalent variable and wxWidgets is version 2.4.2 or above.
            Or this might also be a bug in our configure. Please try again
            with --with-wx-config=/usr/bin/wx-config
            (replace /usr/bin/wx-config with a valid path to your wx-config)
            * Note:
            Most probably, either one of the above aren't correct, you don't
            have wxGTK installed, or are missing wxGTK-devel (or equivalent) package.


```

oh and one more thing: how do i install .packages as well. i have a few of those lying around.

---

### Post by Bachstelze on 2007-05-21
That's because people tell you : "compiling from source is ./configure, make, make install" period, while it is often not the case. There should be a README in your source tarball, read it.

EDIT : I've downloaded xmule just out of curiosity and ./configure && make && sudo make install did the trick for me. Are you *really* sure ./configure ran without errors ?

---

### Post by silentjudas on 2007-05-21
> **HymnToLife said:**
> That's because people tell you : "compiling from source is ./configure, make, make install" period, while it is often not the case. There should be a README in your source tarball, read it.

alright, i did what u said, found that wx whatever i had to install and did so. then i tried again. still no, so i read more, tells me an alt way to do it. same error.....i'll upload the install.txt file

edit: and yes ./configure did have errors, i posted it above, sorry

---

### Post by Bachstelze on 2007-05-21
Please paste the errors you get with ./configure. As long as there will be errors, the Makefile will not be created and you will not be able to build xmule.

---

### Post by silentjudas on 2007-05-21
> **HymnToLife said:**
> Please paste the errors you get with ./configure. As long as there will be errors, the Makefile will not be created and you will not be able to build xmule.

i posted them >.< here they are AGAIN

```

configure: error:
            Please check that wx-config is in path, the directory
            where wxWindows libraries are installed (returned by
            'wx-config --libs' command) is in LD_LIBRARY_PATH or
            equivalent variable and wxWidgets is version 2.4.2 or above.
            Or this might also be a bug in our configure. Please try again
            with --with-wx-config=/usr/bin/wx-config
            (replace /usr/bin/wx-config with a valid path to your wx-config)
            * Note:
            Most probably, either one of the above aren't correct, you don't
            have wxGTK installed, or are missing wxGTK-devel (or equivalent) package.

```

and i installed what i told me and did what i told me >>>>>.<<<<<<

---

### Post by Bachstelze on 2007-05-21
Try to install *libwxgtk2.8-dev*.

---

### Post by silentjudas on 2007-05-21
ok and now i get this

```

checking for wxWidgets static library... no
checking if wxWidgets was linked with GTK2... no
checking for gtk-config... no
checking for GTK - version >= 1.2.0... no
*** The gtk-config script installed by GTK could not be found
*** If GTK was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GTK_CONFIG environment variable to the
*** full path to gtk-config.
checking zlib.h usability... no
checking zlib.h presence... no
checking for zlib.h... no
checking for zlib in peer directory... no
configure: error: unable to use zlib - no peer found


```

---

### Post by helmet on 2007-05-21
sudo aptitude install zlib1g-dev

a good pattern is look for the -dev packages of certain things. it's whining about zlib, so do an aptitude search zlib, and the zlib1g-dev is development related package, so install that, see what happens

---

### Post by silentjudas on 2007-05-21
ok now it worked after installing that...but sudo make install wont work! rawr!

ok, really long sequence of errors, mostly about that wx thingy
i retried make and i got the same errors as well..

```

Size&#8217;
/usr/include/wx-2.6/wx/window.h:246: error: invalid use of undefined type &#8216;const struct wxSize&#8217;
/usr/include/wx-2.6/wx/font.h:34: error: forward declaration of &#8216;const struct wxSize&#8217;
/usr/include/wx-2.6/wx/window.h: In member function &#8216;void wxWindowBase::SetClientSize(int)&#8217;:
/usr/include/wx-2.6/wx/window.h:249: error: &#8216;rect&#8217; was not declared in this scope
/usr/include/wx-2.6/wx/window.h: In member function &#8216;wxPoint wxWindowBase::GetPosition() const&#8217;:
/usr/include/wx-2.6/wx/window.h:254: error: return type &#8216;struct wxPoint&#8217; is incomplete
/usr/include/wx-2.6/wx/window.h:258: error: invalid use of undefined type &#8216;struct wxPoint&#8217;
/usr/include/wx-2.6/wx/utils.h:55: error: forward declaration of &#8216;struct wxPoint&#8217;
/usr/include/wx-2.6/wx/window.h: In member function &#8216;wxSize wxWindowBase::GetSize() const&#8217;:
/usr/include/wx-2.6/wx/window.h:265: error: return type &#8216;struct wxSize&#8217; is incomplete
/usr/include/wx-2.6/wx/window.h:268: error: invalid use of undefined type &#8216;struct wxSize&#8217;
/usr/include/wx-2.6/wx/font.h:34: error: forward declaration of &#8216;struct wxSize&#8217;
/usr/include/wx-2.6/wx/window.h: In member function &#8216;wxSize wxWindowBase::GetClientSize() const&#8217;:
/usr/include/wx-2.6/wx/window.h:282: error: return type &#8216;struct wxSize&#8217; is incomplete
/usr/include/wx-2.6/wx/window.h:286: error: invalid use of undefined type &#8216;struct wxSize&#8217;
/usr/include/wx-2.6/wx/font.h:34: error: forward declaration of &#8216;struct wxSize&#8217;
/usr/include/wx-2.6/wx/window.h: In member function &#8216;wxSize wxWindowBase::GetBestSize() const&#8217;:
/usr/include/wx-2.6/wx/window.h:304: error: return type &#8216;struct wxSize&#8217; is incomplete
/usr/include/wx-2.6/wx/window.h:305: error: &#8216;m_bestSizeCache&#8217; was not declared in this scope
/usr/include/wx-2.6/wx/window.h:307: error: invalid use of undefined type &#8216;struct wxSize&#8217;
/usr/include/wx-2.6/wx/font.h:34: error: forward declaration of &#8216;struct wxSize&#8217;
/usr/include/wx-2.6/wx/window.h: In member function &#8216;void wxWindowBase::GetBestSize(int*, int*) const&#8217;:
/usr/include/wx-2.6/wx/window.h:311: error: variable &#8216;wxSize s&#8217; has initializer but incomplete type
/usr/include/wx-2.6/wx/window.h: In member function &#8216;void wxWindowBase::CacheBestSize(const wxSize&) const&#8217;:
/usr/include/wx-2.6/wx/window.h:322: error: &#8216;class wxWindowBase&#8217; has no member named &#8216;m_bestSizeCache&#8217;
/usr/include/wx-2.6/wx/window.h: In member function &#8216;wxSize wxWindowBase::GetAdjustedBestSize() const&#8217;:
/usr/include/wx-2.6/wx/window.h:330: error: return type &#8216;struct wxSize&#8217; is incomplete
/usr/include/wx-2.6/wx/window.h:331: error: variable &#8216;wxSize s&#8217; has initializer but incomplete type
/usr/include/wx-2.6/wx/window.h:332: error: invalid use of undefined type &#8216;struct wxSize&#8217;
/usr/include/wx-2.6/wx/font.h:34: error: forward declaration of &#8216;struct wxSize&#8217;
/usr/include/wx-2.6/wx/window.h: In member function &#8216;void wxWindowBase::SetSizeHints(const wxSize&, const wxSize&, const wxSize&)&#8217;:
/usr/include/wx-2.6/wx/window.h:376: error: invalid use of undefined type &#8216;const struct wxSize&#8217;
/usr/include/wx-2.6/wx/font.h:34: error: forward declaration of &#8216;const struct wxSize&#8217;
/usr/include/wx-2.6/wx/window.h:376: error: invalid use of undefined type &#8216;const struct wxSize&#8217;
/usr/include/wx-2.6/wx/font.h:34: error: forward declaration of &#8216;const struct wxSize&#8217;
/usr/include/wx-2.6/wx/window.h:377: error: invalid use of undefined type &#8216;const struct wxSize&#8217;
/usr/include/wx-2.6/wx/font.h:34: error: forward declaration of &#8216;const struct wxSize&#8217;
/usr/include/wx-2.6/wx/window.h:377: error: invalid use of undefined type &#8216;const struct wxSize&#8217;
/usr/include/wx-2.6/wx/font.h:34: error: forward declaration of &#8216;const struct wxSize&#8217;
/usr/include/wx-2.6/wx/window.h:378: error: invalid use of undefined type &#8216;const struct wxSize&#8217;
/usr/include/wx-2.6/wx/font.h:34: error: forward declaration of &#8216;const struct wxSize&#8217;
/usr/include/wx-2.6/wx/window.h:378: error: invalid use of undefined type &#8216;const struct wxSize&#8217;
/usr/include/wx-2.6/wx/font.h:34: error: forward declaration of &#8216;const struct wxSize&#8217;
/usr/include/wx-2.6/wx/window.h: In member function &#8216;void wxWindowBase::SetVirtualSizeHints(const wxSize&, const wxSize&)&#8217;:
/usr/include/wx-2.6/wx/window.h:390: error: invalid use of undefined type &#8216;const struct wxSize&#8217;
/usr/include/wx-2.6/wx/font.h:34: error: forward declaration of &#8216;const struct wxSize&#8217;
/usr/include/wx-2.6/wx/window.h:390: error: invalid use of undefined type &#8216;const struct wxSize&#8217;
/usr/include/wx-2.6/wx/font.h:34: error: forward declaration of &#8216;const struct wxSize&#8217;
/usr/include/wx-2.6/wx/window.h:390: error: invalid use of undefined type &#8216;const struct wxSize&#8217;
/usr/include/wx-2.6/wx/font.h:34: error: forward declaration of &#8216;const struct wxSize&#8217;
/usr/include/wx-2.6/wx/window.h:390: error: invalid use of undefined type &#8216;const struct wxSize&#8217;
/usr/include/wx-2.6/wx/font.h:34: error: forward declaration of &#8216;const struct wxSize&#8217;
/usr/include/wx-2.6/wx/window.h: In member function &#8216;virtual wxSize wxWindowBase::GetMaxSize() const&#8217;:
/usr/include/wx-2.6/wx/window.h:399: error: return type &#8216;struct wxSize&#8217; is incomplete
/usr/include/wx-2.6/wx/window.h:399: error: invalid use of undefined type &#8216;struct wxSize&#8217;
/usr/include/wx-2.6/wx/font.h:34: error: forward declaration of &#8216;struct wxSize&#8217;
/usr/include/wx-2.6/wx/window.h: In member function &#8216;virtual wxSize wxWindowBase::GetMinSize() const&#8217;:
/usr/include/wx-2.6/wx/window.h:400: error: return type &#8216;struct wxSize&#8217; is incomplete
/usr/include/wx-2.6/wx/window.h:400: error: invalid use of undefined type &#8216;struct wxSize&#8217;
/usr/include/wx-2.6/wx/font.h:34: error: forward declaration of &#8216;struct wxSize&#8217;
/usr/include/wx-2.6/wx/window.h: In member function &#8216;void wxWindowBase::SetMaxSize(const wxSize&)&#8217;:
/usr/include/wx-2.6/wx/window.h:403: error: invalid use of void expression
/usr/include/wx-2.6/wx/window.h: In member function &#8216;void wxWindowBase::SetVirtualSize(const wxSize&)&#8217;:
/usr/include/wx-2.6/wx/window.h:411: error: invalid use of undefined type &#8216;const struct wxSize&#8217;
/usr/include/wx-2.6/wx/font.h:34: error: forward declaration of &#8216;const struct wxSize&#8217;
/usr/include/wx-2.6/wx/window.h:411: error: invalid use of undefined type &#8216;const struct wxSize&#8217;
/usr/include/wx-2.6/wx/font.h:34: error: forward declaration of &#8216;const struct wxSize&#8217;
/usr/include/wx-2.6/wx/window.h: In member function &#8216;wxSize wxWindowBase::GetVirtualSize() const&#8217;:
/usr/include/wx-2.6/wx/window.h:414: error: return type &#8216;struct wxSize&#8217; is incomplete
/usr/include/wx-2.6/wx/window.h:414: error: invalid use of undefined type &#8216;struct wxSize&#8217;
/usr/include/wx-2.6/wx/font.h:34: error: forward declaration of &#8216;struct wxSize&#8217;
/usr/include/wx-2.6/wx/window.h: In member function &#8216;void wxWindowBase::GetVirtualSize(int*, int*) const&#8217;:
/usr/include/wx-2.6/wx/window.h:417: error: variable &#8216;wxSize s&#8217; has initializer but incomplete type
/usr/include/wx-2.6/wx/window.h:417: error: invalid use of undefined type &#8216;struct wxSize&#8217;
/usr/include/wx-2.6/wx/font.h:34: error: forward declaration of &#8216;struct wxSize&#8217;
/usr/include/wx-2.6/wx/window.h: In member function &#8216;virtual wxSize wxWindowBase::GetBestVirtualSize() const&#8217;:
/usr/include/wx-2.6/wx/window.h:436: error: return type &#8216;struct wxSize&#8217; is incomplete
/usr/include/wx-2.6/wx/window.h:437: error: variable &#8216;wxSize client&#8217; has initializer but incomplete type
/usr/include/wx-2.6/wx/window.h:438: error: variable &#8216;wxSize best&#8217; has initializer but incomplete type
/usr/include/wx-2.6/wx/window.h:440: error: invalid use of undefined type &#8216;struct wxSize&#8217;
/usr/include/wx-2.6/wx/font.h:34: error: forward declaration of &#8216;struct wxSize&#8217;
/usr/include/wx-2.6/wx/window.h: In member function &#8216;wxSize wxWindowBase::ConvertPixelsToDialog(const wxSize&)&#8217;:
/usr/include/wx-2.6/wx/window.h:645: error: return type &#8216;struct wxSize&#8217; is incomplete
/usr/include/wx-2.6/wx/window.h:646: error: variable &#8216;wxPoint pt&#8217; has initializer but incomplete type
/usr/include/wx-2.6/wx/window.h:646: error: invalid use of undefined type &#8216;const struct wxSize&#8217;
/usr/include/wx-2.6/wx/font.h:34: error: forward declaration of &#8216;const struct wxSize&#8217;
/usr/include/wx-2.6/wx/window.h:646: error: invalid use of undefined type &#8216;const struct wxSize&#8217;
/usr/include/wx-2.6/wx/font.h:34: error: forward declaration of &#8216;const struct wxSize&#8217;
/usr/include/wx-2.6/wx/window.h:646: error: invalid use of undefined type &#8216;struct wxPoint&#8217;
/usr/include/wx-2.6/wx/utils.h:55: error: forward declaration of &#8216;struct wxPoint&#8217;
/usr/include/wx-2.6/wx/window.h:648: error: invalid use of undefined type &#8216;struct wxSize&#8217;
/usr/include/wx-2.6/wx/font.h:34: error: forward declaration of &#8216;struct wxSize&#8217;
/usr/include/wx-2.6/wx/window.h: In member function &#8216;wxSize wxWindowBase::ConvertDialogToPixels(const wxSize&)&#8217;:
/usr/include/wx-2.6/wx/window.h:652: error: return type &#8216;struct wxSize&#8217; is incomplete
/usr/include/wx-2.6/wx/window.h:653: error: variable &#8216;wxPoint pt&#8217; has initializer but incomplete type
/usr/include/wx-2.6/wx/window.h:653: error: invalid use of undefined type &#8216;const struct wxSize&#8217;
/usr/include/wx-2.6/wx/font.h:34: error: forward declaration of &#8216;const struct wxSize&#8217;
/usr/include/wx-2.6/wx/window.h:653: error: invalid use of undefined type &#8216;const struct wxSize&#8217;
/usr/include/wx-2.6/wx/font.h:34: error: forward declaration of &#8216;const struct wxSize&#8217;
/usr/include/wx-2.6/wx/window.h:653: error: invalid use of undefined type &#8216;struct wxPoint&#8217;
/usr/include/wx-2.6/wx/utils.h:55: error: forward declaration of &#8216;struct wxPoint&#8217;
/usr/include/wx-2.6/wx/window.h:655: error: invalid use of undefined type &#8216;struct wxSize&#8217;
/usr/include/wx-2.6/wx/font.h:34: error: forward declaration of &#8216;struct wxSize&#8217;
/usr/include/wx-2.6/wx/window.h: In member function &#8216;void wxWindowBase::RefreshRect(int)&#8217;:
/usr/include/wx-2.6/wx/window.h:689: error: &#8216;eraseBackground&#8217; was not declared in this scope
/usr/include/wx-2.6/wx/window.h:689: error: &#8216;rect&#8217; was not declared in this scope
/usr/include/wx-2.6/wx/window.h: In member function &#8216;bool wxWindowBase::IsExposed(const wxPoint&) const&#8217;:
/usr/include/wx-2.6/wx/window.h:721: error: invalid use of undefined type &#8216;const struct wxPoint&#8217;
/usr/include/wx-2.6/wx/utils.h:55: error: forward declaration of &#8216;const struct wxPoint&#8217;
/usr/include/wx-2.6/wx/window.h:721: error: invalid use of undefined type &#8216;const struct wxPoint&#8217;
/usr/include/wx-2.6/wx/utils.h:55: error: forward declaration of &#8216;const struct wxPoint&#8217;
/usr/include/wx-2.6/wx/window.h: In member function &#8216;bool wxWindowBase::IsExposed(int) const&#8217;:
/usr/include/wx-2.6/wx/window.h:723: error: &#8216;rect&#8217; was not declared in this scope
/usr/include/wx-2.6/wx/window.h: In member function &#8216;void wxWindowBase::SetOwnBackgroundColour(int)&#8217;:
/usr/include/wx-2.6/wx/window.h:750: error: &#8216;colour&#8217; was not declared in this scope
/usr/include/wx-2.6/wx/window.h: In member function &#8216;void wxWindowBase::SetOwnForegroundColour(int)&#8217;:
/usr/include/wx-2.6/wx/window.h:766: error: &#8216;colour&#8217; was not declared in this scope
/usr/include/wx-2.6/wx/window.h: In member function &#8216;const wxCursor& wxWindowBase::GetCursor() const&#8217;:
/usr/include/wx-2.6/wx/window.h:794: error: &#8216;m_cursor&#8217; was not declared in this scope
/usr/include/wx-2.6/wx/window.h: In member function &#8216;wxPoint wxWindowBase::ClientToScreen(const wxPoint&) const&#8217;:
/usr/include/wx-2.6/wx/window.h:827: error: return type &#8216;struct wxPoint&#8217; is incomplete
/usr/include/wx-2.6/wx/window.h:828: error: invalid use of undefined type &#8216;const struct wxPoint&#8217;
/usr/include/wx-2.6/wx/utils.h:55: error: forward declaration of &#8216;const struct wxPoint&#8217;
/usr/include/wx-2.6/wx/window.h:828: error: invalid use of undefined type &#8216;const struct wxPoint&#8217;
/usr/include/wx-2.6/wx/utils.h:55: error: forward declaration of &#8216;const struct wxPoint&#8217;
/usr/include/wx-2.6/wx/window.h:831: error: invalid use of undefined type &#8216;struct wxPoint&#8217;
/usr/include/wx-2.6/wx/utils.h:55: error: forward declaration of &#8216;struct wxPoint&#8217;
/usr/include/wx-2.6/wx/window.h: In member function &#8216;wxPoint wxWindowBase::ScreenToClient(const wxPoint&) const&#8217;:
/usr/include/wx-2.6/wx/window.h:835: error: return type &#8216;struct wxPoint&#8217; is incomplete
/usr/include/wx-2.6/wx/window.h:836: error: invalid use of undefined type &#8216;const struct wxPoint&#8217;
/usr/include/wx-2.6/wx/utils.h:55: error: forward declaration of &#8216;const struct wxPoint&#8217;
/usr/include/wx-2.6/wx/window.h:836: error: invalid use of undefined type &#8216;const struct wxPoint&#8217;
/usr/include/wx-2.6/wx/utils.h:55: error: forward declaration of &#8216;const struct wxPoint&#8217;
/usr/include/wx-2.6/wx/window.h:839: error: invalid use of undefined type &#8216;struct wxPoint&#8217;
/usr/include/wx-2.6/wx/utils.h:55: error: forward declaration of &#8216;struct wxPoint&#8217;
/usr/include/wx-2.6/wx/window.h: In member function &#8216;wxHitTest wxWindowBase::HitTest(const wxPoint&) const&#8217;:
/usr/include/wx-2.6/wx/window.h:847: error: invalid use of undefined type &#8216;const struct wxPoint&#8217;
/usr/include/wx-2.6/wx/utils.h:55: error: forward declaration of &#8216;const struct wxPoint&#8217;
/usr/include/wx-2.6/wx/window.h:847: error: invalid use of undefined type &#8216;const struct wxPoint&#8217;
/usr/include/wx-2.6/wx/utils.h:55: error: forward declaration of &#8216;const struct wxPoint&#8217;
/usr/include/wx-2.6/wx/window.h: In member function &#8216;wxWindow* wxWindowBase::GetGrandParent() const&#8217;:
/usr/include/wx-2.6/wx/window.h:1420: error: invalid use of undefined type &#8216;struct wxWindow&#8217;
/usr/include/wx-2.6/wx/utils.h:53: error: forward declaration of &#8216;struct wxWindow&#8217;
/usr/include/wx-2.6/wx/scrolwin.h: At global scope:
/usr/include/wx-2.6/wx/scrolwin.h:96: error: &#8216;wxScrollWinEvent&#8217; has not been declared
/usr/include/wx-2.6/wx/scrolwin.h:105: error: expected &#8216;,&#8217; or &#8216;...&#8217; before &#8216;&&#8217; token
/usr/include/wx-2.6/wx/scrolwin.h:105: error: ISO C++ forbids declaration of &#8216;wxRect&#8217; with no type
/usr/include/wx-2.6/wx/scrolwin.h:106: error: &#8216;wxRect&#8217; does not name a type
/usr/include/wx-2.6/wx/scrolwin.h:126: error: &#8216;wxScrollWinEvent&#8217; has not been declared
/usr/include/wx-2.6/wx/scrolwin.h:129: error: &#8216;wxScrollWinEvent&#8217; has not been declared
/usr/include/wx-2.6/wx/scrolwin.h:130: error: &#8216;wxSizeEvent&#8217; has not been declared
/usr/include/wx-2.6/wx/scrolwin.h:131: error: &#8216;wxPaintEvent&#8217; has not been declared
/usr/include/wx-2.6/wx/scrolwin.h:132: error: &#8216;wxKeyEvent&#8217; has not been declared
/usr/include/wx-2.6/wx/scrolwin.h:133: error: &#8216;wxMouseEvent&#8217; has not been declared
/usr/include/wx-2.6/wx/scrolwin.h:134: error: &#8216;wxMouseEvent&#8217; has not been declared
/usr/include/wx-2.6/wx/scrolwin.h:141: error: &#8216;wxScrollWinEvent&#8217; has not been declared
/usr/include/wx-2.6/wx/scrolwin.h:150: error: ISO C++ forbids declaration of &#8216;wxRect&#8217; with no type
/usr/include/wx-2.6/wx/scrolwin.h:150: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
/usr/include/wx-2.6/wx/scrolwin.h:156: error: expected `;' before &#8216;wxSize&#8217;
/usr/include/wx-2.6/wx/scrolwin.h:184: error: &#8216;wxRect&#8217; does not name a type
/usr/include/wx-2.6/wx/scrolwin.h: In member function &#8216;wxPoint wxScrollHelper::CalcScrolledPosition(const wxPoint&) const&#8217;:
/usr/include/wx-2.6/wx/scrolwin.h:74: error: return type &#8216;struct wxPoint&#8217; is incomplete
/usr/include/wx-2.6/wx/scrolwin.h:75: error: aggregate &#8216;wxPoint p2&#8217; has incomplete type and cannot be defined
/usr/include/wx-2.6/wx/scrolwin.h:76: error: invalid use of undefined type &#8216;const struct wxPoint&#8217;
/usr/include/wx-2.6/wx/utils.h:55: error: forward declaration of &#8216;const struct wxPoint&#8217;
/usr/include/wx-2.6/wx/scrolwin.h:76: error: invalid use of undefined type &#8216;const struct wxPoint&#8217;
/usr/include/wx-2.6/wx/utils.h:55: error: forward declaration of &#8216;const struct wxPoint&#8217;
/usr/include/wx-2.6/wx/scrolwin.h: In member function &#8216;wxPoint wxScrollHelper::CalcUnscrolledPosition(const wxPoint&) const&#8217;:
/usr/include/wx-2.6/wx/scrolwin.h:83: error: return type &#8216;struct wxPoint&#8217; is incomplete
/usr/include/wx-2.6/wx/scrolwin.h:84: error: aggregate &#8216;wxPoint p2&#8217; has incomplete type and cannot be defined
/usr/include/wx-2.6/wx/scrolwin.h:85: error: invalid use of undefined type &#8216;const struct wxPoint&#8217;
/usr/include/wx-2.6/wx/utils.h:55: error: forward declaration of &#8216;const struct wxPoint&#8217;
/usr/include/wx-2.6/wx/scrolwin.h:85: error: invalid use of undefined type &#8216;const struct wxPoint&#8217;
/usr/include/wx-2.6/wx/utils.h:55: error: forward declaration of &#8216;const struct wxPoint&#8217;
/usr/include/wx-2.6/wx/scrolwin.h: In member function &#8216;void wxScrollHelper::SetTargetRect(int)&#8217;:
/usr/include/wx-2.6/wx/scrolwin.h:105: error: &#8216;m_rectToScroll&#8217; was not declared in this scope
/usr/include/wx-2.6/wx/scrolwin.h:105: error: &#8216;rect&#8217; was not declared in this scope
/usr/include/wx-2.6/wx/scrolwin.h: In member function &#8216;wxSize wxScrollHelper::GetTargetSize() const&#8217;:
/usr/include/wx-2.6/wx/scrolwin.h:157: error: return type &#8216;struct wxSize&#8217; is incomplete
/usr/include/wx-2.6/wx/scrolwin.h:158: error: &#8216;m_rectToScroll&#8217; was not declared in this scope
/usr/include/wx-2.6/wx/scrolwin.h:159: error: invalid use of undefined type &#8216;struct wxWindow&#8217;
/usr/include/wx-2.6/wx/utils.h:53: error: forward declaration of &#8216;struct wxWindow&#8217;
/usr/include/wx-2.6/wx/scrolwin.h: In member function &#8216;void wxScrollHelper::GetTargetSize(int*, int*)&#8217;:
/usr/include/wx-2.6/wx/scrolwin.h:164: error: variable &#8216;wxSize size&#8217; has initializer but incomplete type
/usr/include/wx-2.6/wx/generic/panelg.h: At global scope:
/usr/include/wx-2.6/wx/generic/panelg.h:35: error: invalid use of undefined type &#8216;struct wxWindow&#8217;
/usr/include/wx-2.6/wx/utils.h:53: error: forward declaration of &#8216;struct wxWindow&#8217;
/usr/include/wx-2.6/wx/generic/panelg.h:77: error: &#8216;wxSizeEvent&#8217; has not been declared
/usr/include/wx-2.6/wx/generic/panelg.h:86: error: &#8216;wxChildFocusEvent&#8217; has not been declared
/usr/include/wx-2.6/wx/generic/panelg.h:54: error: &#8216;wxDefaultPosition&#8217; was not declared in this scope
/usr/include/wx-2.6/wx/generic/panelg.h:55: error: &#8216;wxDefaultSize&#8217; was not declared in this scope
/usr/include/wx-2.6/wx/generic/panelg.h:66: error: &#8216;wxDefaultPosition&#8217; was not declared in this scope
/usr/include/wx-2.6/wx/generic/panelg.h:67: error: &#8216;wxDefaultSize&#8217; was not declared in this scope
/usr/include/wx-2.6/wx/generic/panelg.h: In constructor &#8216;wxPanel::wxPanel(wxWindow*, int, int, int, int, long int, const wxString&)&#8217;:
/usr/include/wx-2.6/wx/generic/panelg.h:48: error: invalid use of undefined type &#8216;struct wxPoint&#8217;
/usr/include/wx-2.6/wx/utils.h:55: error: forward declaration of &#8216;struct wxPoint&#8217;
/usr/include/wx-2.6/wx/generic/panelg.h:48: error: invalid use of undefined type &#8216;struct wxSize&#8217;
/usr/include/wx-2.6/wx/font.h:34: error: forward declaration of &#8216;struct wxSize&#8217;
/usr/include/wx-2.6/wx/generic/scrolwin.h: At global scope:
/usr/include/wx-2.6/wx/generic/scrolwin.h:88: error: &#8216;wxPaintEvent&#8217; has not been declared
/usr/include/wx-2.6/wx/generic/scrolwin.h:52: error: &#8216;wxDefaultPosition&#8217; was not declared in this scope
/usr/include/wx-2.6/wx/generic/scrolwin.h:53: error: &#8216;wxDefaultSize&#8217; was not declared in this scope
/usr/include/wx-2.6/wx/generic/scrolwin.h:65: error: &#8216;wxDefaultPosition&#8217; was not declared in this scope
/usr/include/wx-2.6/wx/generic/scrolwin.h:66: error: &#8216;wxDefaultSize&#8217; was not declared in this scope
/usr/include/wx-2.6/wx/generic/scrolwin.h: In constructor &#8216;wxGenericScrolledWindow::wxGenericScrolledWindow()&#8217;:
/usr/include/wx-2.6/wx/generic/scrolwin.h:49: error: no matching function for call to &#8216;wxScrollHelper::wxScrollHelper(wxGenericScrolledWindow* const)&#8217;
/usr/include/wx-2.6/wx/scrolwin.h:206: note: candidates are: wxScrollHelper::wxScrollHelper(const wxScrollHelper&)
/usr/include/wx-2.6/wx/scrolwin.h:31: note:                 wxScrollHelper::wxScrollHelper(wxWindow*)
/usr/include/wx-2.6/wx/generic/scrolwin.h: In constructor &#8216;wxGenericScrolledWindow::wxGenericScrolledWindow(wxWindow*, wxWindowID, const wxPoint&, const wxSize&, long int, const wxString&)&#8217;:
/usr/include/wx-2.6/wx/generic/scrolwin.h:56: error: no matching function for call to &#8216;wxScrollHelper::wxScrollHelper(wxGenericScrolledWindow* const)&#8217;
/usr/include/wx-2.6/wx/scrolwin.h:206: note: candidates are: wxScrollHelper::wxScrollHelper(const wxScrollHelper&)
/usr/include/wx-2.6/wx/scrolwin.h:31: note:                 wxScrollHelper::wxScrollHelper(wxWindow*)
/usr/include/wx-2.6/wx/scrolwin.h: At global scope:
/usr/include/wx-2.6/wx/scrolwin.h:226: error: &#8216;wxDefaultPosition&#8217; was not declared in this scope
/usr/include/wx-2.6/wx/scrolwin.h:227: error: &#8216;wxDefaultSize&#8217; was not declared in this scope
../../src/wxTreeMultiCtrl.h:299: error: expected class-name before &#8216;{&#8217; token
../../src/wxTreeMultiCtrl.h:310: error: ISO C++ forbids declaration of &#8216;wxCommandEvent&#8217; with no type
../../src/wxTreeMultiCtrl.h:310: error: &#8216;wxCommandEvent&#8217; declared as a &#8216;virtual&#8217; field
../../src/wxTreeMultiCtrl.h:310: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
../../src/wxTreeMultiCtrl.h:312: error: expected `;' before &#8216;wxTreeMultiItem&#8217;
../../src/wxTreeMultiCtrl.h: In constructor &#8216;wxTreeMultiEvent::wxTreeMultiEvent(const wxEventType&)&#8217;:
../../src/wxTreeMultiCtrl.h:306: error: class &#8216;wxTreeMultiEvent&#8217; does not have any field named &#8216;wxNotifyEvent&#8217;
../../src/wxTreeMultiCtrl.h: At global scope:
../../src/wxTreeMultiCtrl.h:553: error: ISO C++ forbids declaration of &#8216;wxBitmap&#8217; with no type
../../src/wxTreeMultiCtrl.h:553: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
../../src/wxTreeMultiCtrl.h:605: error: expected &#8216;,&#8217; or &#8216;...&#8217; before &#8216;&&#8217; token
../../src/wxTreeMultiCtrl.h:605: error: ISO C++ forbids declaration of &#8216;wxColour&#8217; with no type
../../src/wxTreeMultiCtrl.h:642: error: field &#8216;_captionFont&#8217; has incomplete type
../../src/wxTreeMultiCtrl.h:656: error: &#8216;wxPaintEvent&#8217; has not been declared
../../src/wxTreeMultiCtrl.h:657: error: &#8216;wxMouseEvent&#8217; has not been declared
../../src/wxTreeMultiCtrl.h:658: error: &#8216;wxKeyEvent&#8217; has not been declared
../../src/wxTreeMultiCtrl.h:677: error: &#8216;wxDefaultPosition&#8217; was not declared in this scope
../../src/wxTreeMultiCtrl.h:678: error: &#8216;wxDefaultSize&#8217; was not declared in this scope
../../src/wxTreeMultiCtrl.h:697: error: &#8216;wxDefaultPosition&#8217; was not declared in this scope
../../src/wxTreeMultiCtrl.h:698: error: &#8216;wxDefaultSize&#8217; was not declared in this scope
../../src/wxTreeMultiCtrl.h: In member function &#8216;void wxTreeMultiCtrl::DeleteAllItems()&#8217;:
../../src/wxTreeMultiCtrl.h:740: error: &#8216;Refresh&#8217; was not declared in this scope
../../src/wxTreeMultiCtrl.h: In member function &#8216;void wxTreeMultiCtrl::Fold(const wxTreeMultiItem&, bool)&#8217;:
../../src/wxTreeMultiCtrl.h:782: error: cannot convert &#8216;wxTreeMultiCtrl* const&#8217; to &#8216;wxEvtHandler*&#8217; for argument &#8216;1&#8217; to &#8216;void wxPostEvent(wxEvtHandler*, wxEvent&)&#8217;
../../src/wxTreeMultiCtrl.h: In member function &#8216;const wxFont& wxTreeMultiCtrl::GetCaptionFont() const&#8217;:
../../src/wxTreeMultiCtrl.h:992: error: &#8216;_captionFont&#8217; was not declared in this scope
DynPrefsCtrl.h: At global scope:
DynPrefsCtrl.h:61: error: &#8216;wxCommandEvent&#8217; has not been declared
DynPrefsCtrl.h:62: error: &#8216;wxCommandEvent&#8217; has not been declared
DynPrefsCtrl.h:64: error: &#8216;wxCommandEvent&#8217; has not been declared
DynPrefsCtrl.h:65: error: &#8216;wxCommandEvent&#8217; has not been declared
DynPrefsCtrl.h:66: error: &#8216;wxScrollEvent&#8217; has not been declared
DynPrefsCtrl.h:57: error: &#8216;wxDefaultPosition&#8217; was not declared in this scope
DynPrefsCtrl.h:57: error: &#8216;wxDefaultSize&#8217; was not declared in this scope
/usr/include/wx-2.6/wx/toplevel.h:119: error: invalid use of undefined type &#8216;struct wxWindow&#8217;
/usr/include/wx-2.6/wx/utils.h:53: error: forward declaration of &#8216;struct wxWindow&#8217;
/usr/include/wx-2.6/wx/toplevel.h:196: error: &#8216;wxCloseEvent&#8217; has not been declared
/usr/include/wx-2.6/wx/toplevel.h:197: error: &#8216;wxSizeEvent&#8217; has not been declared
/usr/include/wx-2.6/wx/toplevel.h:204: error: &#8216;wxActivateEvent&#8217; has not been declared
/usr/include/wx-2.6/wx/toplevel.h:207: error: &#8216;wxUpdateUIEvent&#8217; has not been declared
/usr/include/wx-2.6/wx/toplevel.h: In member function &#8216;virtual bool wxTopLevelWindowBase::IsActive()&#8217;:
/usr/include/wx-2.6/wx/toplevel.h:180: error: &#8216;FindFocus&#8217; was not declared in this scope
/usr/include/wx-2.6/wx/frame.h: At global scope:
/usr/include/wx-2.6/wx/frame.h:58: error: expected class-name before &#8216;{&#8217; token
/usr/include/wx-2.6/wx/dialog.h:37: error: expected class-name before &#8216;{&#8217; token
/usr/include/wx-2.6/wx/dialog.h:80: error: &#8216;wxChildFocusEvent&#8217; has not been declared
/usr/include/wx-2.6/wx/sizer.h: In member function &#8216;void wxSizerItem::SetMinSize(const wxSize&)&#8217;:
/usr/include/wx-2.6/wx/sizer.h:200: error: invalid use of undefined type &#8216;struct wxWindow&#8217;
/usr/include/wx-2.6/wx/utils.h:53: error: forward declaration of &#8216;struct wxWindow&#8217;
DynamicPreferencesCtrl.cpp: At global scope:
DynamicPreferencesCtrl.cpp:92: error: &#8216;wxNotifyEventFunction&#8217; was not declared in this scope
DynamicPreferencesCtrl.cpp:93: error: &#8216;wxCommandEventHandler&#8217; was not declared in this scope
DynamicPreferencesCtrl.cpp:94: error: &#8216;EVT_TEXT&#8217; was not declared in this scope
DynamicPreferencesCtrl.cpp:95: error: expected `}' before &#8216;wxEventTableEntry&#8217;
DynamicPreferencesCtrl.cpp:95: error: expected &#8216;,&#8217; or &#8216;;&#8217; before &#8216;wxEventTableEntry&#8217;
DynamicPreferencesCtrl.cpp:97: error: expected declaration before &#8216;}&#8217; token
make[1]: *** [obj/DynamicPreferencesCtrl.o] Error 1
make: *** [all] Error 2

```

---

### Post by taurus on 2007-05-21
Did you remember to run "**make**" first before you ran "sudo make install"?

---

### Post by silentjudas on 2007-05-21
yes. it worked the first time. then i ran s.m.i. and it bombed, then i re-ran make and the same error popped....
i shall now ./c again
edit: ok re ./c and it did so, then i make'd and it error-ed again! ughhhhhhhhhhhh!

forget that. i'm re extracting the tar and trying again


edit2: ok...re did it...still erroring, mostly yet again about that wx thingy. what is it!

---

### Post by WW on 2007-05-21
What is the *first* error that occurs when you run **make**?

---

### Post by silentjudas on 2007-05-21
runs to fast for me to get to the first one. i go up and it starts about half way.
first one i can get to is
```

regroundColour(int)&#8217;:
/usr/include/wx-2.6/wx/window.h:766: error: &#8216;colour&#8217; was not declared in this scope

```

---

### Post by silentjudas on 2007-05-21
everyone else stuck too...?:confused::(

---

### Post by WW on 2007-05-21
Try this command:
```

make > msgs

```
and then use your favorite editor to look at the file called **msgs**.

---

### Post by silentjudas on 2007-05-22
and where did that file go? (aka save to)

---

### Post by Outrunner on 2007-05-22
Probably in your home folder /home/username

---

### Post by WW on 2007-05-22
> **silentjudas said:**
> and where did that file go? (aka save to)

In the same directory where you ran the make command.  You can use gedit, for example.
```

make > msgs
gedit msgs &

```

---

### Post by silentjudas on 2007-05-22
this is all i get from those

==== Building Precompiled Headers ====
src/xmule-headers.h.gch

that all it gave me in the msgs file

---

