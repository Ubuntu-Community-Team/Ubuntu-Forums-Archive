---
title: "Firefox Dialog text"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by richtechie on 2008-03-27
Whenever a dialog box appears from my Firefox browser (2.0.0.13), the text is white which makes it hard to read. This also happens in the Edit --> Preferences area.

Any ideas on how to fix these issues?

---

### Post by cisforcojo on 2008-03-27
Are you running a GNOME/GTK theme?

---

### Post by richtechie on 2008-03-28
Yes, I believe so. I am a new Ubtuntu user running version 7.10. Thanks for the help!

---

### Post by cisforcojo on 2008-03-30
Did you solve your problem? I had similar problems with text readability when I was trying to select a 'dark' theme for Ubuntu.

---

### Post by richtechie on 2008-03-31
No, I have not found a solution. I am using a GNOME theme. Thanks for the help.

---

### Post by cisforcojo on 2008-04-01
Do you have the problem in other programs or is it just a Firefox problem?
Could you post a screenshot? (Applications -> Accessories -> Take Screenshot)

Next question: Are you running Beryl or Compiz-Fusion? That can sometimes create problems like you're describing.

---

### Post by richtechie on 2008-04-01
No, I am not running Beryl or Compiz-Fusion. Here is a screenshot. I appreciate the responses. Thanks!!

---

### Post by cisforcojo on 2008-04-02
The screenshot was exactly what I needed. It's a problem with your Firefox theme. I'll bet if you change the theme, the text in the dialog boxes becomes readable again. You have 2 choices.
1) Change your Firefox theme
2) Change your Ubuntu theme (this involves more work)
    [http://www.gnome-look.org](http://www.gnome-look.org) can help you find a suitable dark theme.
    System->Preferences->Appearance should let you configure your GNOME appearance

Since your Firefox theme is dark, it's assuming that your entire desktop is dark. Thus the light text in the dialog boxes.

---

### Post by kerry_s on 2008-04-02
you need to use userChrome.css to change those text colors.

menubar, menubutton, menu, menuitem, menupopup, popup > * {
color: #fffbff !important;
}

---

### Post by richtechie on 2008-04-07
Thanks!! I changed my Firefox theme to a lighter theme and everything looks great!

---

### Post by cisforcojo on 2008-04-08
Sure! Glad to help.

---

