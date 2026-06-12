---
title: "Error starting Amule"
date: 2006-02-24
forum: Absolute Beginner Talk
---

### Post by isenalim on 2006-02-24
Hi,
I have some troubles with amule. The version available from the Breezy repositories freeze the computer a few minutes after it starts, so I tried to install version 2.1.0: first downloading some precompiled package and then with Automatix. In any case, when launching amule I get this long list of messages and then amule doesn't start.
Thank you very much for any help,
Bye
B

mule: Symbol `_ZTV11wxSpinEvent' has different size in shared object, consider re-linking
amule: Symbol `_ZTV14wxTextCtrlBase' has different size in shared object, consider re-linking
amule: Symbol `_ZTV18wxControlWithItems' has different size in shared object, consider re-linking
amule: Symbol `_ZTV16wxDatagramSocket' has different size in shared object, consider re-linking
amule: Symbol `_ZTV8wxSlider' has different size in shared object, consider re-linking
amule: Symbol `_ZTV14wxSocketServer' has different size in shared object, consider re-linking
amule: Symbol `_ZTV7wxTimer' has different size in shared object, consider re-linking
amule: Symbol `_ZTV14wxCommandEvent' has different size in shared object, consider re-linking
amule: Symbol `_ZTV12wxChoiceBase' has different size in shared object, consider re-linking
amule: Symbol `_ZTV11wxGDIObject' has different size in shared object, consider re-linking
amule: Symbol `_ZTV18wxGenericValidator' has different size in shared object, consider re-linking
amule: Symbol `_ZTV20wxNavigationKeyEvent' has different size in shared object, consider re-linking
amule: Symbol `_ZTV12wxFocusEvent' has different size in shared object, consider re-linking
amule: Symbol `_ZTI7wxSizer' has different size in shared object, consider re-linking
amule: Symbol `_ZTV13wxControlBase' has different size in shared object, consider re-linking
amule: Symbol `_ZTV6wxMenu' has different size in shared object, consider re-linking
amule: Symbol `_ZTV7wxImage' has different size in shared object, consider re-linking
amule: Symbol `_ZTV13wxScrollEvent' has different size in shared object, consider re-linking
amule: Symbol `_ZTV17wxGenericListCtrl' has different size in shared object, consider re-linking
amule: Symbol `_ZTV16wxScrolledWindow' has different size in shared object, consider re-linking
amule: Symbol `_ZTV13wxSocketEvent' has different size in shared object, consider re-linking
amule: Symbol `_ZTV10wxTreeCtrl' has different size in shared object, consider re-linking
amule: Symbol `_ZTV10wxListItem' has different size in shared object, consider re-linking
amule: Symbol `_ZTV12wxTimerEvent' has different size in shared object, consider re-linking
amule: Symbol `_ZTV7wxGauge' has different size in shared object, consider re-linking
amule: Symbol `_ZTV10wxListBase' has different size in shared object, consider re-linking
amule: Symbol `_ZTV12wxBitmapBase' has different size in shared object, consider re-linking
amule: Symbol `_ZTV10wxFontBase' has different size in shared object, consider re-linking
amule: Symbol `_ZTV10wxRadioBox' has different size in shared object, consider re-linking
amule: Symbol `_ZTV8wxChoice' has different size in shared object, consider re-linking
amule: Symbol `_ZTV11wxListEvent' has different size in shared object, consider re-linking
amule: Symbol `_ZTV11wxImageList' has different size in shared object, consider re-linking
amule: Symbol `_ZTV8wxObject' has different size in shared object, consider re-linking
amule: Symbol `_ZTV10wxClientDC' has different size in shared object, consider re-linking
amule: Symbol `_ZTV13wxNotifyEvent' has different size in shared object, consider re-linking
amule: Symbol `_ZTV11wxTimerBase' has different size in shared object, consider re-linking
amule: Symbol `_ZTV15wxNotebookEvent' has different size in shared object, consider re-linking
amule: Symbol `_ZTV5wxPen' has different size in shared object, consider re-linking
amule: Symbol `_ZTV10wxMenuBase' has different size in shared object, consider re-linking
amule: Symbol `_ZTV14wxBitmapButton' has different size in shared object, consider re-linking
amule: Symbol `_ZTV16wxZipInputStream' has different size in shared object, consider re-linking
amule: Symbol `_ZTV6wxList' has different size in shared object, consider re-linking
amule: Symbol `_ZTV7wxFrame' has different size in shared object, consider re-linking
amule: Symbol `_ZTV8wxButton' has different size in shared object, consider re-linking
amule: Symbol `_ZTV10wxTextCtrl' has different size in shared object, consider re-linking
amule: Symbol `_ZTV8wxBitmap' has different size in shared object, consider re-linking
amule: Symbol `_ZTV6wxFont' has different size in shared object, consider re-linking
amule: Symbol `_ZTV7wxEvent' has different size in shared object, consider re-linking
amule: Symbol `_ZTV12wxCloseEvent' has different size in shared object, consider re-linking
amule: Symbol `_ZTV6wxIcon' has different size in shared object, consider re-linking
amule: Symbol `_ZTV10wxSpinCtrl' has different size in shared object, consider re-linking
amule: Symbol `_ZTV10wxCheckBox' has different size in shared object, consider re-linking
amule: Symbol `_ZTV18wxGenericImageList' has different size in shared object, consider re-linking
amule: Symbol `_ZTV16wxSplitterWindow' has different size in shared object, consider re-linking
amule: Symbol `_ZTV9wxControl' has different size in shared object, consider re-linking
amule: Symbol `_ZTV12wxDialogBase' has different size in shared object, consider re-linking
amule: Symbol `_ZTV10wxKeyEvent' has different size in shared object, consider re-linking
amule: Symbol `_ZTV16wxTopLevelWindow' has different size in shared object, consider re-linking
amule: Symbol `_ZTV7wxBrush' has different size in shared object, consider re-linking
amule: Symbol `_ZTV12wxMouseEvent' has different size in shared object, consider re-linking
amule: Symbol `_ZTV7wxPanel' has different size in shared object, consider re-linking
amule: Symbol `_ZTV8wxDialog' has different size in shared object, consider re-linking
amule: Symbol `_ZTV10wxListCtrl' has different size in shared object, consider re-linking
amule: Symbol `_ZTV8wxColour' has different size in shared object, consider re-linking
amule: Symbol `_ZTV9wxPaintDC' has different size in shared object, consider re-linking
amule: Symbol `_ZTV17wxGenericTreeCtrl' has different size in shared object, consider re-linking
Segmentation fault

---

### Post by gord on 2006-02-24
it sounds you have a newer version of a libary that amule depends on, than was compiled with amule (looks like wxWidgets too me). id suggest either reverting to the older version or compiling your own version of amule from the amule website.

---

### Post by isenalim on 2006-02-25
Hi,
I tried to compile amule by myself but I can't locate the libwxbase2.6-dev.
Do you know where i can get it?
Thanks

---

