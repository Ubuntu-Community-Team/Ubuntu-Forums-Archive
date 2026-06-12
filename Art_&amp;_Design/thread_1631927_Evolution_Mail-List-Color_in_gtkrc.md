---
title: "Evolution Mail-List-Color in gtkrc?"
date: 2010-11-27
forum: Art &amp; Design
---

### Post by t.rei on 2010-11-27
Hi,

I am currently working on a rather light theme for my desktop and the one thing that really drives me nuts right now ist, that in evolution, in the Middle-Column in the Vertical Layout Mode where the Mails are all listed, the *_selected background color_ *is waaay too light. 
I tortured google for a while now, but can't seem to find the right hack. I tried about anything I could find.

If anyone can give me advice, I'd gladly take it.

Thanks.

---

### Post by t.rei on 2010-11-27
Solution (loooong trial and error hunting...) this was insane... but ok, found it:

style "murrine-notebook-layout" = "murrine-default"
{
    bg[ACTIVE]        = @selected_bg_color #evolution mail-list evo-unfocussed item.
    bg[SELECTED]    = @selected_bg_color #evolution mail-list-evo-focussed item.
    engine "murrine" {
        roundness = 3
    }
}
widget_class "*<GtkNotebook>*<GtkLayout>"       style "murrine-notebook-layout"

Yep, looks like evolution is using some kind of Tab for this... or something. at least this is what makes it use proper background colors for the selected items.

---

