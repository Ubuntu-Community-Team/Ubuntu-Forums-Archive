---
title: "Applications menu is empty"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by fred22 on 2006-08-26
Hi All,

Installed xubuntu last night on an old laptop and am very pleased indeed. Although I did spend 5 hours trying to sort out the resolution of the screen.

Can anyone help with current problem?

I have somehow 'cleared' the applications menu that used to display when clicking the applications button on top left of screen. Did this trying to set up a new application launcher I think. Now it does nothing at all when clicked

Is there an easy way of restoring the contents?

Thanks in advance

---

### Post by fred22 on 2006-08-26
OK found out the following:got the following good advice from [www.ubuntuforums.org/archive/index.php/t-184984.html+xfce4+menu+editor+open+menu&hl=en&gl=uk&ct=clnk&cd=3](www.ubuntuforums.org/archive/index.php/t-184984.html+xfce4+menu+editor+open+menu&hl=en&gl=uk&ct=clnk&cd=3)

it seems to be a common problem, the above can simply be done with the following command:
cp /etc/xdg/xfce4/desktop/menu.xml ~/.config/xfce4/desktop/menu.xml

---

