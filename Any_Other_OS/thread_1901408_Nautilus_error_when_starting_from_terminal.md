---
title: "Nautilus error when starting from terminal"
date: 2011-12-28
forum: Any Other OS
---

### Post by Rubicon421 on 2011-12-28
whenever I launch Nautilus from the terminal, I get a huge list of errors in the terminal, but then nautilus opens and runs fine. Nautilus also works normally when started from the menu and everything seems to work, but the errors are concerning. Anyone know what's going on here? 

```
(nautilus:17569): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_menu_shell_insert: assertion `GTK_IS_MENU_SHELL (menu_shell)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_widget_get_parent: assertion `GTK_IS_WIDGET (widget)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_widget_get_parent: assertion `GTK_IS_WIDGET (widget)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_widget_get_parent: assertion `GTK_IS_WIDGET (widget)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_widget_get_parent: assertion `GTK_IS_WIDGET (widget)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_widget_get_parent: assertion `GTK_IS_WIDGET (widget)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_widget_get_parent: assertion `GTK_IS_WIDGET (widget)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_widget_get_parent: assertion `GTK_IS_WIDGET (widget)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_image_menu_item_set_always_show_image: assertion `GTK_IS_IMAGE_MENU_ITEM (image_menu_item)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_widget_get_parent: assertion `GTK_IS_WIDGET (widget)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_menu_item_get_submenu: assertion `GTK_IS_MENU_ITEM (menu_item)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_widget_get_parent: assertion `GTK_IS_WIDGET (widget)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed

(nautilus:17569): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed

(nautilus:17569): Gtk-CRITICAL **: find_menu_position: assertion `GTK_IS_MENU_SHELL (menushell)' failed
^C

```I'm running Linux Mint 12 x86 with GNOME Shell and Nautilus 3.2.1

---

### Post by oldos2er on 2011-12-28
Moved to Other OS/Distro Talk.

---

### Post by legendbb on 2012-08-31
Xilinx SDK on Ubuntu 11.10

similar situation, after googling, tried $ sudo ./{the_app}, it starts without error.

So it seems to me permission related. 

Original error message:

```
(Xilinx SDK:4027): LIBDBUSMENU-GTK-CRITICAL **: watch_submenu: assertion `GTK_IS_MENU_SHELL(menu)' failed
...

```

Don't know the cause.

---

### Post by Bachstelze on 2012-08-31
It's very common to see such messages when running GUI (especially GTK) apps from the terminal. I don't know the exact cause since I'm not a GTK person, but you can safely ignore them.

---

