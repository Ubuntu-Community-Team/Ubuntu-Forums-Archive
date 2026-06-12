---
title: "Installing XPDE"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by ProjectWhat on 2006-10-02
I need help installing the them XPDE.
[http://www.xpde.com/]("http://www.xpde.com/")
When i try to install it it says that its not the right format. Please help. Thank you.

---

### Post by Sef on 2006-10-02
Read this: [How to install anything.]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by orb9220 on 2006-10-02
[http://www.psychocats.net/ubuntu/xpde](http://www.psychocats.net/ubuntu/xpde)

---

### Post by ProjectWhat on 2006-10-02
I tried the [http://www.psychocats.net/ubuntu/xpde]("http://www.psychocats.net/ubuntu/xpde") link but it did not work. Is it because I have ubuntu and not kubuntu?

---

### Post by orb9220 on 2006-10-02
After installing did you reboot and at login screen go to options and change session?

---

### Post by aysiu on 2006-10-02
Can you be more specific than "it did not work"?

It should have absolutely nothing to do with having Ubuntu or Kubuntu.

What was the output of these commands? ```
chmod +x installxpde.sh
./installxpde.sh
``` Do not *describe* the output--post the output. Copy and paste everything from the terminal to a post here.

It should look something like this: ```
username@ubuntu:~$ **cd Desktop**
username@ubuntu:~/Desktop$ **chmod +x installxpde.sh**
username@ubuntu:~/Desktop$ **./installxpde.sh**
--19:48:25--  http://www.xpde.com/releases/xpde-0.5.1.tar.gz
           => `xpde-0.5.1.tar.gz'
Resolving www.xpde.com... 212.34.136.33
Connecting to www.xpde.com|212.34.136.33|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4,726,057 (4.5M) [application/x-tar]

100%[=================================================================================================================>] 4,726,057    124.97K/s    ETA 00:00

19:49:00 (139.99 KB/s) - `xpde-0.5.1.tar.gz' saved [4726057/4726057]

Password:
xpde/
xpde/bin/
xpde/bin/applets/
xpde/bin/applets/desktop_properties
xpde/bin/defaultdesktop/
xpde/bin/defaultdesktop/Desktop/
xpde/bin/defaultdesktop/Desktop/browser.lnk
xpde/bin/defaultdesktop/Desktop/command line.lnk
xpde/bin/defaultdesktop/Desktop/gimp.lnk
xpde/bin/defaultdesktop/Themes/
xpde/bin/defaultdesktop/Themes/Luna/
xpde/bin/defaultdesktop/Themes/Luna/Frame/
xpde/bin/defaultdesktop/Themes/Luna/Frame/captionbar_active.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/captionbar_inactive.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/captionbar_left_active.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/captionbar_left_inactive.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/captionbar_right_active.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/captionbar_right_inactive.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/captionbutton_mask.bmp
xpde/bin/defaultdesktop/Themes/Luna/Frame/captionbutton_mask.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/captionbutton_normal.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/captionbutton_over.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/captionbutton_press.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/close_active_disable.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/close_active_normal.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/close_active_over.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/close_active_press.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/frame_mask_left.bmp
xpde/bin/defaultdesktop/Themes/Luna/Frame/frame_mask_right.bmp
xpde/bin/defaultdesktop/Themes/Luna/Frame/framebottom_active.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/framebottom_inactive.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/framebottom_left_active.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/framebottom_left_inactive.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/framebottom_right_active.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/framebottom_right_inactive.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/frameleft_active.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/frameleft_inactive.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/frameright_active.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/frameright_inactive.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/maximize_active_disable.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/maximize_active_normal.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/maximize_active_over.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/maximize_active_press.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/minimize_active_disable.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/minimize_active_normal.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/minimize_active_over.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/minimize_active_press.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/restore_active_disable.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/restore_active_normal.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/restore_active_over.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/restore_active_press.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/
xpde/bin/defaultdesktop/Themes/Luna/Icons/32x32/
xpde/bin/defaultdesktop/Themes/Luna/Icons/32x32/browser.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/32x32/command_line.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/32x32/folder.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/32x32/gimp.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/32x32/mycomputer.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/32x32/mydocuments.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/32x32/myhome.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/32x32/mynetworkplaces.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/32x32/noicon.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/32x32/recyclebin_empty.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/32x32/recyclebin_full.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/32x32/source.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/32x32/aim.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/32x32/mypictures.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/32x32/mymusic.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/32x32/myrecentdocuments.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/32x32/controlpanel.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/32x32/printers.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/32x32/help.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/32x32/run.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/32x32/search.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/32x32/email.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/32x32/calc.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/32x32/notepad.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/programs_folder.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/email.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/menu_subitems.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/browser.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/aim.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/narrator.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/mplayer.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/notepad.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/command_prompt.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/compatibility_wizard.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/calculator.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/address_book.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/paint.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/backup.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/wordpad.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/file_explorer.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/xpde_tour.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/magnifier.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/synchronize.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/remote_assistance.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/accessibility_wizard.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/on_screen_keyboard.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/utility_manager.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/hyperterminal.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/sound_recorder.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/network_setup_wizard.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/network_connections.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/new_connection_wizard.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/remote_desktop_connection.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/volume_control.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/character_map.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/disk_cleanup.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/disk_defragmenter.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/scheduled_tasks.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/files_and_settings_transfer_wizard.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/system_information.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/system_restore.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/22x22/
xpde/bin/defaultdesktop/Themes/Luna/Icons/22x22/browser.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/22x22/gimp.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/22x22/command_line.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/22x22/controlpanel.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/22x22/folder.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/22x22/run.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/22x22/help.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/22x22/mycomputer.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/22x22/mymusic.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/22x22/mydocuments.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/22x22/myhome.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/22x22/mynetworkplaces.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/22x22/mypictures.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/22x22/myrecentdocuments.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/22x22/noicon.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/22x22/printers.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/22x22/recyclebin_empty.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/22x22/recyclebin_full.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/22x22/search.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/22x22/source.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/22x22/menu_right.png
xpde/bin/defaultdesktop/Themes/Luna/Misc/
xpde/bin/defaultdesktop/Themes/Luna/Misc/noglyph.png
xpde/bin/defaultdesktop/Themes/Luna/Misc/bmp.png
xpde/bin/defaultdesktop/Themes/Luna/Misc/jpg.png
xpde/bin/defaultdesktop/Themes/Luna/Misc/desktoppropertiesmonitor.png
xpde/bin/defaultdesktop/Themes/Luna/Misc/none.png
xpde/bin/defaultdesktop/Themes/Luna/Misc/png.png
xpde/bin/defaultdesktop/Themes/Luna/Taskbar/
xpde/bin/defaultdesktop/Themes/Luna/Taskbar/no_icon.png
xpde/bin/defaultdesktop/Themes/Luna/Taskbar/st_normal.png
xpde/bin/defaultdesktop/Themes/Luna/Taskbar/st_over.png
xpde/bin/defaultdesktop/Themes/Luna/Taskbar/st_press.png
xpde/bin/defaultdesktop/Themes/Luna/Taskbar/start_button_normal.png
xpde/bin/defaultdesktop/Themes/Luna/Taskbar/start_button_over.png
xpde/bin/defaultdesktop/Themes/Luna/Taskbar/start_button_press.png
xpde/bin/defaultdesktop/Themes/Luna/Taskbar/taskband_button_normal.png
xpde/bin/defaultdesktop/Themes/Luna/Taskbar/taskband_button_over.png
xpde/bin/defaultdesktop/Themes/Luna/Taskbar/taskband_button_press.png
xpde/bin/defaultdesktop/Themes/Luna/Taskbar/taskbar_background_bottom.png
xpde/bin/defaultdesktop/Themes/Luna/Taskbar/taskbar_grip_vert.png
xpde/bin/defaultdesktop/Themes/Luna/Taskbar/taskbar_language_es.png
xpde/bin/defaultdesktop/Themes/Luna/Taskbar/taskbar_separator.png
xpde/bin/defaultdesktop/Themes/Luna/Wallpapers/
xpde/bin/defaultdesktop/Themes/Luna/Wallpapers/default.png
xpde/bin/defaultdesktop/Themes/Luna/Arrows.bmp
xpde/bin/defaultdesktop/Themes/Luna/Button.bmp
xpde/bin/defaultdesktop/Themes/Luna/CheckBox.bmp
xpde/bin/defaultdesktop/Themes/Luna/ComboBox.bmp
xpde/bin/defaultdesktop/Themes/Luna/EditText.bmp
xpde/bin/defaultdesktop/Themes/Luna/GroupBox.bmp
xpde/bin/defaultdesktop/Themes/Luna/Header.bmp
xpde/bin/defaultdesktop/Themes/Luna/ProgressBar.bmp
xpde/bin/defaultdesktop/Themes/Luna/RadioButton.bmp
xpde/bin/defaultdesktop/Themes/Luna/ScrollBar.bmp
xpde/bin/defaultdesktop/Themes/Luna/TabBody.bmp
xpde/bin/defaultdesktop/Themes/Luna/Tabs.bmp
xpde/bin/defaultdesktop/Themes/Luna/ToolBarButton.bmp
xpde/bin/defaultdesktop/Themes/Luna/ToolBarSep.bmp
xpde/bin/defaultdesktop/Themes/Luna/TrackBar.bmp
xpde/bin/defaultdesktop/Themes/Luna/StartMenu/
xpde/bin/defaultdesktop/Themes/Luna/StartMenu/startmenu_user_panel.png
xpde/bin/defaultdesktop/Themes/Luna/StartMenu/startmenu_places.png
xpde/bin/defaultdesktop/Themes/Luna/StartMenu/startmenu_logoff.png
xpde/bin/defaultdesktop/Themes/Luna/StartMenu/startmenu_mfu.png
xpde/bin/defaultdesktop/Themes/Luna/StartMenu/startmenu_programs.png
xpde/bin/defaultdesktop/Themes/Luna/StartMenu/startmenu_separator.png
xpde/bin/defaultdesktop/Themes/Luna/StartMenu/user_tile.png
xpde/bin/defaultdesktop/Themes/Luna/StartMenu/startmenu_logoff_normal.png
xpde/bin/defaultdesktop/Themes/Luna/StartMenu/startmenu_logoff_over.png
xpde/bin/defaultdesktop/Themes/Luna/StartMenu/startmenu_sleep_normal.png
xpde/bin/defaultdesktop/Themes/Luna/StartMenu/startmenu_sleep_over.png
xpde/bin/defaultdesktop/Themes/Luna/StartMenu/startmenu_turnoff_normal.png
xpde/bin/defaultdesktop/Themes/Luna/StartMenu/startmenu_turnoff_over.png
xpde/bin/defaultdesktop/Themes/Luna/StartMenu/startmenu_options_background.png
xpde/bin/defaultdesktop/Start Menu/
xpde/bin/defaultdesktop/Start Menu/Programs/
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/Accessibility/
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/Accessibility/Utility Manager.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/Accessibility/Narrator.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/Accessibility/Magnifier.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/Accessibility/Accesibility Wizard.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/Accessibility/On-Screen Keyboard.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/Communications/
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/Communications/New Connection Wizard.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/Communications/Network Setup Wizard.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/Communications/Remote Desktop Connection.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/Communications/Network Connections.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/Communications/HyperTerminal.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/Entertainment/
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/Entertainment/Volume Control.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/Entertainment/Sound Recorder.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/Entertainment/MPlayer.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/System Tools/
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/System Tools/System Restore.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/System Tools/Backup.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/System Tools/Disk Defragmenter.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/System Tools/System Information.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/System Tools/Character Map.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/System Tools/Disk Cleanup.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/System Tools/Scheduled Tasks.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/System Tools/Files and Settings Transfer Wizard.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/Program Compatibility Wizard.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/Notepad.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/Calculator.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/File Explorer.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/Address Book.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/Paint.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/XPde Tour.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/Synchronize.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/WordPad.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/Command Prompt.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Administrative Tools/
xpde/bin/defaultdesktop/Start Menu/Programs/Startup/
xpde/bin/defaultdesktop/Start Menu/Programs/Games/
xpde/bin/defaultdesktop/Start Menu/Programs/Internet Browser.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Email.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/MPlayer.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/AIM.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Remote Assistance.lnk
xpde/bin/bplXPColorSelect.so
xpde/bin/startxpde
xpde/bin/xpde
xpde/bin/libborqt-6.9-qt2.3.so
xpde/src/
xpde/src/core/
xpde/src/core/xpde.kof
xpde/src/core/xpde.dpr
xpde/src/core/xpde.conf
xpde/src/core/xpde.res
xpde/src/core/main.pas
xpde/src/core/main.xfm
xpde/src/core/main.ddp
xpde/src/core/uXPDesktop.pas
xpde/src/core/xpde.desk
xpde/src/core/uWMConsts.pas
xpde/src/core/uXPTaskbar.pas
xpde/src/core/uXPStartButton.pas
xpde/src/core/uXPSysTray.pas
xpde/src/core/uXPTaskband.pas
xpde/src/core/uWindowManager.pas
xpde/src/core/uActiveTasks.pas
xpde/src/core/uActiveTasks.xfm
xpde/src/core/uXPStyledFrame.ddp
xpde/src/core/uXPStyledFrame.pas
xpde/src/core/uXPStyledFrame.xfm
xpde/src/core/uXPStartMenu.ddp
xpde/src/core/uXPStartMenu.pas
xpde/src/core/uXPStartMenu.xfm
xpde/src/core/uXPMenu.ddp
xpde/src/core/uXPMenu.pas
xpde/src/core/uXPMenu.xfm
xpde/src/core/uTaskbar.pas
xpde/src/core/uTaskbar.xfm
xpde/src/core/uTaskbar.ddp
xpde/src/components/
xpde/src/components/XPColorSelect/
xpde/src/components/XPColorSelect/XPColorSelect.conf
xpde/src/components/XPColorSelect/XPColorSelect.dpk
xpde/src/components/XPColorSelect/XPColorSelect.kof
xpde/src/components/XPColorSelect/XPColorSelect.res
xpde/src/components/XPColorSelect/uXPColorDialog.pas
xpde/src/components/XPColorSelect/uXPColorDialog.xfm
xpde/src/components/XPColorSelect/uXPColorSelector.pas
xpde/src/components/XPColorSelect/XPColorSelect.dcp
xpde/src/components/XPColorSelect/uXPColorDialog.ddp
xpde/src/components/XPDirectoryMonitor/
xpde/src/components/XPDirectoryMonitor/uXPDirectoryMonitor.pas
xpde/src/components/XPImageList/
xpde/src/components/XPImageList/uXPImageList.pas
xpde/src/components/XPListView/
xpde/src/components/XPListView/listview.txt
xpde/src/components/XPListView/uXPListView.pas
xpde/src/components/XPListView/uXPListView_orig.pas
xpde/src/components/XPRegistry/
xpde/src/components/XPRegistry/RegLib.pas
xpde/src/components/XPRegistry/uRegLib.pas
xpde/src/components/XPRegistry/uRegistry.pas
xpde/src/components/XPShellListView/
xpde/src/components/XPShellListView/uXPShellListView.pas
xpde/src/common/
xpde/src/common/QTheming/
xpde/src/common/QTheming/Themes/
xpde/src/common/QTheming/Themes/Luna/
xpde/src/common/QTheming/Themes/Luna/Arrows.bmp
xpde/src/common/QTheming/Themes/Luna/Button.bmp
xpde/src/common/QTheming/Themes/Luna/CheckBox.bmp
xpde/src/common/QTheming/Themes/Luna/ComboBox.bmp
xpde/src/common/QTheming/Themes/Luna/EditText.bmp
xpde/src/common/QTheming/Themes/Luna/GroupBox.bmp
xpde/src/common/QTheming/Themes/Luna/Header.bmp
xpde/src/common/QTheming/Themes/Luna/ProgressBar.bmp
xpde/src/common/QTheming/Themes/Luna/RadioButton.bmp
xpde/src/common/QTheming/Themes/Luna/ScrollBar.bmp
xpde/src/common/QTheming/Themes/Luna/TabBody.bmp
xpde/src/common/QTheming/Themes/Luna/Tabs.bmp
xpde/src/common/QTheming/Themes/Luna/ToolBarButton.bmp
xpde/src/common/QTheming/Themes/Luna/ToolBarSep.bmp
xpde/src/common/QTheming/Themes/Luna/TrackBar.bmp
xpde/src/common/QTheming/Compilers.inc
xpde/src/common/QTheming/QThemeSrv.pas
xpde/src/common/QTheming/QThemeSrvLinux.pas
xpde/src/common/QTheming/QThemed.pas
xpde/src/common/QTheming/QTheming.txt
xpde/src/common/QTheming/QTmSchema.pas
xpde/src/common/QTheming/QUxTheme.pas
xpde/src/common/QTheming/ReadmeKylix.txt
xpde/src/common/QTheming/winxp.res
xpde/src/common/uCommon.pas
xpde/src/common/uGraphics.pas
xpde/src/common/uResample.pas
xpde/src/common/uXPIPC.pas
xpde/src/common/uXPPNG.pas
xpde/src/applets/
xpde/src/applets/desktop_properties/
xpde/src/applets/desktop_properties/desktop_properties.conf
xpde/src/applets/desktop_properties/desktop_properties.dpr
xpde/src/applets/desktop_properties/desktop_properties.kof
xpde/src/applets/desktop_properties/desktop_properties.res
xpde/src/applets/desktop_properties/uDisplayProperties.pas
xpde/src/applets/desktop_properties/uDisplayProperties.xfm
xpde/src/xpde_group.bpg
xpde/src/xpde_group.desk
xpde/INSTALL
--19:49:22--  http://www.psychocats.net/ubuntu/XPde.desktop
           => `XPde.desktop'
Resolving www.psychocats.net... 64.14.68.87
Connecting to www.psychocats.net|64.14.68.87|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 126 [text/plain]

100%[=================================================================================================================>] 126           --.--K/s

19:49:23 (8.58 MB/s) - `XPde.desktop' saved [126/126]

In order for your changes to take effect, press Control-Alt-Backspace or reboot.
username@ubuntu:~/Desktop$
```

---

### Post by ProjectWhat on 2006-10-02
I tried this 
```
chmod +x installxpde.sh
./installxpde.sh
```
and it says:
```
admin@admin-desktop:~$ chmod +x installxpde.sh
chmod: cannot access `installxpde.sh': No such file or directory

```
But when I use the code of the link it says this:
```
admin@admin-desktop:~$ cd ~/Desktop
admin@admin-desktop:~/Desktop$ chmod +x installxpde.sh
admin@admin-desktop:~/Desktop$ ./installxpde.sh
--21:50:57--  http://www.xpde.com/releases/xpde-0.5.1.tar.gz
           => `xpde-0.5.1.tar.gz'
Resolving www.xpde.com... 212.34.136.33
Connecting to www.xpde.com|212.34.136.33|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4,726,057 (4.5M) [application/x-tar]

100%[====================================>] 4,726,057    497.99K/s    ETA 00:00

21:51:07 (483.82 KB/s) - `xpde-0.5.1.tar.gz' saved [4726057/4726057]

Password:
xpde/
xpde/bin/
xpde/bin/applets/
xpde/bin/applets/desktop_properties
xpde/bin/defaultdesktop/
xpde/bin/defaultdesktop/Desktop/
xpde/bin/defaultdesktop/Desktop/browser.lnk
xpde/bin/defaultdesktop/Desktop/command line.lnk
xpde/bin/defaultdesktop/Desktop/gimp.lnk
xpde/bin/defaultdesktop/Themes/
xpde/bin/defaultdesktop/Themes/Luna/
xpde/bin/defaultdesktop/Themes/Luna/Frame/
xpde/bin/defaultdesktop/Themes/Luna/Frame/captionbar_active.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/captionbar_inactive.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/captionbar_left_active.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/captionbar_left_inactive.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/captionbar_right_active.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/captionbar_right_inactive.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/captionbutton_mask.bmp
xpde/bin/defaultdesktop/Themes/Luna/Frame/captionbutton_mask.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/captionbutton_normal.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/captionbutton_over.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/captionbutton_press.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/close_active_disable.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/close_active_normal.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/close_active_over.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/close_active_press.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/frame_mask_left.bmp
xpde/bin/defaultdesktop/Themes/Luna/Frame/frame_mask_right.bmp
xpde/bin/defaultdesktop/Themes/Luna/Frame/framebottom_active.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/framebottom_inactive.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/framebottom_left_active.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/framebottom_left_inactive.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/framebottom_right_active.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/framebottom_right_inactive.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/frameleft_active.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/frameleft_inactive.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/frameright_active.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/frameright_inactive.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/maximize_active_disable.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/maximize_active_normal.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/maximize_active_over.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/maximize_active_press.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/minimize_active_disable.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/minimize_active_normal.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/minimize_active_over.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/minimize_active_press.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/restore_active_disable.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/restore_active_normal.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/restore_active_over.png
xpde/bin/defaultdesktop/Themes/Luna/Frame/restore_active_press.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/
xpde/bin/defaultdesktop/Themes/Luna/Icons/32x32/
xpde/bin/defaultdesktop/Themes/Luna/Icons/32x32/browser.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/32x32/command_line.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/32x32/folder.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/32x32/gimp.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/32x32/mycomputer.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/32x32/mydocuments.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/32x32/myhome.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/32x32/mynetworkplaces.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/32x32/noicon.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/32x32/recyclebin_empty.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/32x32/recyclebin_full.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/32x32/source.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/32x32/aim.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/32x32/mypictures.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/32x32/mymusic.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/32x32/myrecentdocuments.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/32x32/controlpanel.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/32x32/printers.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/32x32/help.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/32x32/run.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/32x32/search.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/32x32/email.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/32x32/calc.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/32x32/notepad.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/programs_folder.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/email.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/menu_subitems.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/browser.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/aim.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/narrator.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/mplayer.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/notepad.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/command_prompt.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/compatibility_wizard.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/calculator.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/address_book.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/paint.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/backup.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/wordpad.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/file_explorer.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/xpde_tour.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/magnifier.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/synchronize.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/remote_assistance.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/accessibility_wizard.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/on_screen_keyboard.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/utility_manager.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/hyperterminal.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/sound_recorder.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/network_setup_wizard.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/network_connections.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/new_connection_wizard.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/remote_desktop_connection.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/volume_control.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/character_map.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/disk_cleanup.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/disk_defragmenter.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/scheduled_tasks.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/files_and_settings_transfer_wizard.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/system_information.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/16x16/system_restore.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/22x22/
xpde/bin/defaultdesktop/Themes/Luna/Icons/22x22/browser.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/22x22/gimp.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/22x22/command_line.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/22x22/controlpanel.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/22x22/folder.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/22x22/run.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/22x22/help.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/22x22/mycomputer.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/22x22/mymusic.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/22x22/mydocuments.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/22x22/myhome.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/22x22/mynetworkplaces.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/22x22/mypictures.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/22x22/myrecentdocuments.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/22x22/noicon.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/22x22/printers.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/22x22/recyclebin_empty.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/22x22/recyclebin_full.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/22x22/search.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/22x22/source.png
xpde/bin/defaultdesktop/Themes/Luna/Icons/22x22/menu_right.png
xpde/bin/defaultdesktop/Themes/Luna/Misc/
xpde/bin/defaultdesktop/Themes/Luna/Misc/noglyph.png
xpde/bin/defaultdesktop/Themes/Luna/Misc/bmp.png
xpde/bin/defaultdesktop/Themes/Luna/Misc/jpg.png
xpde/bin/defaultdesktop/Themes/Luna/Misc/desktoppropertiesmonitor.png
xpde/bin/defaultdesktop/Themes/Luna/Misc/none.png
xpde/bin/defaultdesktop/Themes/Luna/Misc/png.png
xpde/bin/defaultdesktop/Themes/Luna/Taskbar/
xpde/bin/defaultdesktop/Themes/Luna/Taskbar/no_icon.png
xpde/bin/defaultdesktop/Themes/Luna/Taskbar/st_normal.png
xpde/bin/defaultdesktop/Themes/Luna/Taskbar/st_over.png
xpde/bin/defaultdesktop/Themes/Luna/Taskbar/st_press.png
xpde/bin/defaultdesktop/Themes/Luna/Taskbar/start_button_normal.png
xpde/bin/defaultdesktop/Themes/Luna/Taskbar/start_button_over.png
xpde/bin/defaultdesktop/Themes/Luna/Taskbar/start_button_press.png
xpde/bin/defaultdesktop/Themes/Luna/Taskbar/taskband_button_normal.png
xpde/bin/defaultdesktop/Themes/Luna/Taskbar/taskband_button_over.png
xpde/bin/defaultdesktop/Themes/Luna/Taskbar/taskband_button_press.png
xpde/bin/defaultdesktop/Themes/Luna/Taskbar/taskbar_background_bottom.png
xpde/bin/defaultdesktop/Themes/Luna/Taskbar/taskbar_grip_vert.png
xpde/bin/defaultdesktop/Themes/Luna/Taskbar/taskbar_language_es.png
xpde/bin/defaultdesktop/Themes/Luna/Taskbar/taskbar_separator.png
xpde/bin/defaultdesktop/Themes/Luna/Wallpapers/
xpde/bin/defaultdesktop/Themes/Luna/Wallpapers/default.png
xpde/bin/defaultdesktop/Themes/Luna/Arrows.bmp
xpde/bin/defaultdesktop/Themes/Luna/Button.bmp
xpde/bin/defaultdesktop/Themes/Luna/CheckBox.bmp
xpde/bin/defaultdesktop/Themes/Luna/ComboBox.bmp
xpde/bin/defaultdesktop/Themes/Luna/EditText.bmp
xpde/bin/defaultdesktop/Themes/Luna/GroupBox.bmp
xpde/bin/defaultdesktop/Themes/Luna/Header.bmp
xpde/bin/defaultdesktop/Themes/Luna/ProgressBar.bmp
xpde/bin/defaultdesktop/Themes/Luna/RadioButton.bmp
xpde/bin/defaultdesktop/Themes/Luna/ScrollBar.bmp
xpde/bin/defaultdesktop/Themes/Luna/TabBody.bmp
xpde/bin/defaultdesktop/Themes/Luna/Tabs.bmp
xpde/bin/defaultdesktop/Themes/Luna/ToolBarButton.bmp
xpde/bin/defaultdesktop/Themes/Luna/ToolBarSep.bmp
xpde/bin/defaultdesktop/Themes/Luna/TrackBar.bmp
xpde/bin/defaultdesktop/Themes/Luna/StartMenu/
xpde/bin/defaultdesktop/Themes/Luna/StartMenu/startmenu_user_panel.png
xpde/bin/defaultdesktop/Themes/Luna/StartMenu/startmenu_places.png
xpde/bin/defaultdesktop/Themes/Luna/StartMenu/startmenu_logoff.png
xpde/bin/defaultdesktop/Themes/Luna/StartMenu/startmenu_mfu.png
xpde/bin/defaultdesktop/Themes/Luna/StartMenu/startmenu_programs.png
xpde/bin/defaultdesktop/Themes/Luna/StartMenu/startmenu_separator.png
xpde/bin/defaultdesktop/Themes/Luna/StartMenu/user_tile.png
xpde/bin/defaultdesktop/Themes/Luna/StartMenu/startmenu_logoff_normal.png
xpde/bin/defaultdesktop/Themes/Luna/StartMenu/startmenu_logoff_over.png
xpde/bin/defaultdesktop/Themes/Luna/StartMenu/startmenu_sleep_normal.png
xpde/bin/defaultdesktop/Themes/Luna/StartMenu/startmenu_sleep_over.png
xpde/bin/defaultdesktop/Themes/Luna/StartMenu/startmenu_turnoff_normal.png
xpde/bin/defaultdesktop/Themes/Luna/StartMenu/startmenu_turnoff_over.png
xpde/bin/defaultdesktop/Themes/Luna/StartMenu/startmenu_options_background.png
xpde/bin/defaultdesktop/Start Menu/
xpde/bin/defaultdesktop/Start Menu/Programs/
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/Accessibility/
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/Accessibility/Utility Manager.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/Accessibility/Narrator.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/Accessibility/Magnifier.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/Accessibility/Accesibility Wizard.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/Accessibility/On-Screen Keyboard.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/Communications/
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/Communications/New Connection Wizard.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/Communications/Network Setup Wizard.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/Communications/Remote Desktop Connection.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/Communications/Network Connections.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/Communications/HyperTerminal.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/Entertainment/
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/Entertainment/Volume Control.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/Entertainment/Sound Recorder.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/Entertainment/MPlayer.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/System Tools/
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/System Tools/System Restore.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/System Tools/Backup.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/System Tools/Disk Defragmenter.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/System Tools/System Information.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/System Tools/Character Map.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/System Tools/Disk Cleanup.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/System Tools/Scheduled Tasks.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/System Tools/Files and Settings Transfer Wizard.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/Program Compatibility Wizard.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/Notepad.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/Calculator.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/File Explorer.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/Address Book.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/Paint.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/XPde Tour.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/Synchronize.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/WordPad.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Accessories/Command Prompt.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Administrative Tools/
xpde/bin/defaultdesktop/Start Menu/Programs/Startup/
xpde/bin/defaultdesktop/Start Menu/Programs/Games/
xpde/bin/defaultdesktop/Start Menu/Programs/Internet Browser.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Email.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/MPlayer.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/AIM.lnk
xpde/bin/defaultdesktop/Start Menu/Programs/Remote Assistance.lnk
xpde/bin/bplXPColorSelect.so
xpde/bin/startxpde
xpde/bin/xpde
xpde/bin/libborqt-6.9-qt2.3.so
xpde/src/
xpde/src/core/
xpde/src/core/xpde.kof
xpde/src/core/xpde.dpr
xpde/src/core/xpde.conf
xpde/src/core/xpde.res
xpde/src/core/main.pas
xpde/src/core/main.xfm
xpde/src/core/main.ddp
xpde/src/core/uXPDesktop.pas
xpde/src/core/xpde.desk
xpde/src/core/uWMConsts.pas
xpde/src/core/uXPTaskbar.pas
xpde/src/core/uXPStartButton.pas
xpde/src/core/uXPSysTray.pas
xpde/src/core/uXPTaskband.pas
xpde/src/core/uWindowManager.pas
xpde/src/core/uActiveTasks.pas
xpde/src/core/uActiveTasks.xfm
xpde/src/core/uXPStyledFrame.ddp
xpde/src/core/uXPStyledFrame.pas
xpde/src/core/uXPStyledFrame.xfm
xpde/src/core/uXPStartMenu.ddp
xpde/src/core/uXPStartMenu.pas
xpde/src/core/uXPStartMenu.xfm
xpde/src/core/uXPMenu.ddp
xpde/src/core/uXPMenu.pas
xpde/src/core/uXPMenu.xfm
xpde/src/core/uTaskbar.pas
xpde/src/core/uTaskbar.xfm
xpde/src/core/uTaskbar.ddp
xpde/src/components/
xpde/src/components/XPColorSelect/
xpde/src/components/XPColorSelect/XPColorSelect.conf
xpde/src/components/XPColorSelect/XPColorSelect.dpk
xpde/src/components/XPColorSelect/XPColorSelect.kof
xpde/src/components/XPColorSelect/XPColorSelect.res
xpde/src/components/XPColorSelect/uXPColorDialog.pas
xpde/src/components/XPColorSelect/uXPColorDialog.xfm
xpde/src/components/XPColorSelect/uXPColorSelector.pas
xpde/src/components/XPColorSelect/XPColorSelect.dcp
xpde/src/components/XPColorSelect/uXPColorDialog.ddp
xpde/src/components/XPDirectoryMonitor/
xpde/src/components/XPDirectoryMonitor/uXPDirectoryMonitor.pas
xpde/src/components/XPImageList/
xpde/src/components/XPImageList/uXPImageList.pas
xpde/src/components/XPListView/
xpde/src/components/XPListView/listview.txt
xpde/src/components/XPListView/uXPListView.pas
xpde/src/components/XPListView/uXPListView_orig.pas
xpde/src/components/XPRegistry/
xpde/src/components/XPRegistry/RegLib.pas
xpde/src/components/XPRegistry/uRegLib.pas
xpde/src/components/XPRegistry/uRegistry.pas
xpde/src/components/XPShellListView/
xpde/src/components/XPShellListView/uXPShellListView.pas
xpde/src/common/
xpde/src/common/QTheming/
xpde/src/common/QTheming/Themes/
xpde/src/common/QTheming/Themes/Luna/
xpde/src/common/QTheming/Themes/Luna/Arrows.bmp
xpde/src/common/QTheming/Themes/Luna/Button.bmp
xpde/src/common/QTheming/Themes/Luna/CheckBox.bmp
xpde/src/common/QTheming/Themes/Luna/ComboBox.bmp
xpde/src/common/QTheming/Themes/Luna/EditText.bmp
xpde/src/common/QTheming/Themes/Luna/GroupBox.bmp
xpde/src/common/QTheming/Themes/Luna/Header.bmp
xpde/src/common/QTheming/Themes/Luna/ProgressBar.bmp
xpde/src/common/QTheming/Themes/Luna/RadioButton.bmp
xpde/src/common/QTheming/Themes/Luna/ScrollBar.bmp
xpde/src/common/QTheming/Themes/Luna/TabBody.bmp
xpde/src/common/QTheming/Themes/Luna/Tabs.bmp
xpde/src/common/QTheming/Themes/Luna/ToolBarButton.bmp
xpde/src/common/QTheming/Themes/Luna/ToolBarSep.bmp
xpde/src/common/QTheming/Themes/Luna/TrackBar.bmp
xpde/src/common/QTheming/Compilers.inc
xpde/src/common/QTheming/QThemeSrv.pas
xpde/src/common/QTheming/QThemeSrvLinux.pas
xpde/src/common/QTheming/QThemed.pas
xpde/src/common/QTheming/QTheming.txt
xpde/src/common/QTheming/QTmSchema.pas
xpde/src/common/QTheming/QUxTheme.pas
xpde/src/common/QTheming/ReadmeKylix.txt
xpde/src/common/QTheming/winxp.res
xpde/src/common/uCommon.pas
xpde/src/common/uGraphics.pas
xpde/src/common/uResample.pas
xpde/src/common/uXPIPC.pas
xpde/src/common/uXPPNG.pas
xpde/src/applets/
xpde/src/applets/desktop_properties/
xpde/src/applets/desktop_properties/desktop_properties.conf
xpde/src/applets/desktop_properties/desktop_properties.dpr
xpde/src/applets/desktop_properties/desktop_properties.kof
xpde/src/applets/desktop_properties/desktop_properties.res
xpde/src/applets/desktop_properties/uDisplayProperties.pas
xpde/src/applets/desktop_properties/uDisplayProperties.xfm
xpde/src/xpde_group.bpg
xpde/src/xpde_group.desk
xpde/INSTALL
--21:52:35--  http://www.psychocats.net/ubuntu/XPde.desktop
           => `XPde.desktop'
Resolving www.psychocats.net... 64.14.68.87
Connecting to www.psychocats.net|64.14.68.87|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 126 [text/plain]

100%[====================================>] 126           --.--K/s

21:52:35 (3.16 MB/s) - `XPde.desktop' saved [126/126]

In order for your changes to take effect, press Control-Alt-Backspace or reboot.admin@admin-desktop:~/Desktop$

```
Any Clue?

[edit]
yes i did reboot
[/edit]

---

### Post by aysiu on 2006-10-02
So the first error you got was the file not existing because you were in /home/admin instead of /home/admin/Desktop

The second time, it installed just fine. Now hit Control-Alt-Backspace, click on Sessions and you should see XPDe as an option.

---

### Post by ProjectWhat on 2006-10-02
Ok to get to seesion I go to:
system-->
         Prefrences-->
                      Sessions.

Right is that how I do it because I see nothing about xpde.

---

### Post by sumguy231 on 2006-10-02
That would be 'sessions' on the GDM login screen, rather.

---

### Post by aysiu on 2006-10-02
> **ProjectWhat said:**
> Ok to get to seesion I go to:
system-->
         Prefrences-->
                      Sessions.

Right is that how I do it because I see nothing about xpde. No, not that session. The session at the login screen.

---

### Post by ProjectWhat on 2006-10-02
Oh ok gosh I wish I wasnt such A noob.

---

### Post by aysiu on 2006-10-02
> **ProjectWhat said:**
> Oh ok gosh I wish I wasnt such A noob.
I don't see what the big deal is. There are two (at least) kinds of sessions... you didn't know which one I was talking about. That's okay.

You ask questions... and you get answers.

---

### Post by ProjectWhat on 2006-10-02
This sucks, I tried it and it gave me errors. It also said something about how it lasted for 10 seconds. Oh well, do you know of any other sleek XP look alike themes?

---

### Post by aysiu on 2006-10-02
I hate that stupid 10 seconds error. That can be solved by a reboot, I think.

How about Smooth-XP?
[http://www.gnome-look.org/content/show.php?content=16732](http://www.gnome-look.org/content/show.php?content=16732)

---

### Post by aysiu on 2006-10-02
Alternatively, you can look into IceWM. It may take you a bit to get it up and running quite the way you like, but as far as theming goes, it has Windows look-alikes built right in.

If you're interested in IceWM, I recommend you check out [this thread](http://ubuntuforums.org/showthread.php?t=263710).

---

### Post by ProjectWhat on 2006-10-02
on the silver xp do i want the single or double tar file?

---

### Post by aysiu on 2006-10-02
> **ProjectWhat said:**
> on the silver xp do i want the single or double tar file?
I'm not sure I know what you're asking.

---

### Post by ProjectWhat on 2006-10-02
go [here]("http://sourceforge.net/project/showfiles.php?group_id=83774&package_id=86283&release_id=284924") and look at the links one says single one says double. Whats the difference? I went ahead and took double cause it had more dowloads.

---

### Post by aysiu on 2006-10-02
Well, first of all, IceWM is an entire desktop environment. It isn't just a theme. Silver-XP, however, is a theme that you don't need to download separately.

Do this: ```
sudo aptitude update && sudo aptitude install icewm icewm-themes
``` Then log out, go to Session and pick IceWM. Log in again and click on the IceWM "start" menu (it won't really say *start* on it) and select Themes > S > Silver-XP

---

### Post by ProjectWhat on 2006-10-03
I think Im going to stick with the original. I didnt like that theme. Really disliked it. But anyways I am sorry for the trouble man.

---

