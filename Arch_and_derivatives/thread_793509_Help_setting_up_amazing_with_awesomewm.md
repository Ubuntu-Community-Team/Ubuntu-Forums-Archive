---
title: "Help setting up amazing with awesomewm"
date: 2008-05-13
forum: Arch and derivatives
---

### Post by PurposeOfReason on 2008-05-13
I installed awesome3-git and amazing-git with the config branch and my .amazing/config.rb looks like this
```

module Helpers::PangoMarkup
  def urgent(text)
    foreground("#ff5656", text)
  end
  def normal(text)
    foreground("#888888", text)
  end
  def white(text)
    foreground("#ffffff", text)
  end
end
 
awesome {
  set :statusbar => "top"
 
  widget("battery") {
    set :interval => 10
 
    property("text") {
      dir = ""
      if @state == :charging
        dir = "^"
      elsif @state == :discharging
        dir = "v"
      else
        dir = "="
      end
 
      if @percentage <= 20
        urgent(" #{dir}#{@percentage.to_i}#{dir} ")
      else
        normal(" #{dir}#{@percentage.to_i}#{dir} ")
      end
    }
  }
 
  widget("mpd") {
    set :interval => 1
 
    property("text") {
      case @state
        when :playing : txt = ">>:"; show_info = true
        when :paused : txt = "||:"; show_info = true
        else show_info = false
      end
      if show_info
        " #{txt} #@artist - #@title (#@position/#@length) "
      else # Player is stopped or connection not initialized
        " []: not playing "
      end
    }
  }
 
  widget("gmail") {
    set :interval => 5.minutes
    set :username => "purposeofreason"
    set :password => "CENSORED"
 
    property("text") {
      if @count > 0
        urgent(" #@count")
      else
        normal(" 0")
      end
    }
  }
 
  widget("pacman") {
    set :interval => 1.hours
 
    property("text") {
      if @count > 0
        urgent(" #@count ")
      else
        normal(" 0 ")
      end
    }
  }
 
  widget("clock") {
    set :interval => 1
    set :format => " %T %d.%m.%Y "
  }
 
  widget("cpu_usage") {
    set :interval => 2
    set :module => :noop
 
    property("text") {
      percents = Statgrab.new.cpu_percents
      if percents[:user] >= 50
        urgent(" %.1f%% " % percents[:user])
      else
        white(" %.1f%% " % percents[:user])
      end
    }
  }
 
  widget("cpu_freq") {
    set :module => :cpu_info
    set :interval => 3
 
    property ("text") {
      ghz = @speed[0] / 1000
      if @speed[0] >= 1000
        urgent("@ %1.06fGHz " % ghz)
      else
        normal("@ #{@speed[0].to_i}MHz ")
      end
    }
  }
}

```

.awesomerc
```
screen 0
{
    general
    {
        border = 3
        snap = 8
        mwfact_lower_limit = 0.1
        mwfact_upper_limit = 0.9
        resize_hints = false
        new_get_focus = true
        new_become_master = false
        floating_placement = smart
        opacity_unfocused = 0.9
    }
    styles
    {
        normal
        {
            font = "Myriad Pro 8"
            fg = "#B7A67A"
            bg = "#3D352A"
            border = "#3D352A"
        }
        focus
        {
            fg = "#3D352A"
            bg = "#B7A67A"
            border = "#B7A67A"
        }
        urgent
        {
            fg = "#111111"
            bg = "#ff4500"
        }
    }
    tags
    {
        tag main { layout = "tile" mwfact = 0.7 }
        tag work { }
        tag float { layout = "floating" }
    }
    layouts
    {
        layout tile { image = "/usr/share/awesome/icons/layouts/tilew.png" }
        layout tileleft { image = "/usr/share/awesome/icons/layouts/tileleftw.png" }
        layout tilebottom { image = "/usr/share/awesome/icons/layouts/tilebottomw.png" }
        layout tiletop { image = "/usr/share/awesome/icons/layouts/tiletopw.png" }
        layout max { image = "/usr/share/awesome/icons/layouts/maxw.png" }
        layout spiral { image = "/usr/share/awesome/icons/layouts/spiralw.png" }
        layout dwindle { image = "/usr/share/awesome/icons/layouts/dwindlew.png" }
        layout floating { image = "/usr/share/awesome/icons/layouts/floatingw.png" }
    }
    statusbar mystatusbar
    {
        position = "top"
        height = "16"

        taglist mytaglist
        {
            mouse { button = "1" command = "tag_view" }
            mouse { button = "1" modkey = {"Mod4"} command = "client_tag" }
            mouse { button = "3" command = "tag_toggleview" }
            mouse { button = "3" modkey = {"Mod4"} command = "client_toggletag" }
            mouse { button = "4" command = "tag_viewnext" }
            mouse { button = "5" command = "tag_viewprev" }
        }
        layoutinfo mylayoutinfo
        {
            mouse { button = "1" command = "tag_setlayout" args = {"+1"} }
            mouse { button = "4" command = "tag_setlayout" args = {"+1"} }
            mouse { button = "3" command = "tag_setlayout" args = {"-1"} }
            mouse { button = "5" command = "tag_setlayout" args = {"-1"} }
        }

        textbox battery
        {
            align = "right"
        }
        iconbox ib_start { align = "right" image = "/home/shawn/.awesome/dzen_bitmaps/dzen_bitmaps/mail.png" resize = "true" }
        textbox gmail
        {
            mouse { button = "1" command = "spawn" args = {"amazing -u gmail/top/0"} }
            align = "right"
        }
        textbox pacman
        {
            align = "right"
            mouse { button = "1" command = "spawn" args = {"amazing -u pacman/top/0"} }
        }

        textbox mpd
        {
            align = "right"
            mouse { button = "1" command = "spawn" args = {"mpc toggle"} }
        }

        textbox clock
        {
            align = "right"
        }

    }
}

rules
{
    rule { name = "Gimp" tags = "float" float = "true" }
    rule { name = "Pidgin" tags = "float" float = "true" }
    rule { name = "MPlayer" tags = "float" float = "true" }
    rule { name = "Acroread" float = true }
    rule { name = "pinentry" float = true }
    rule { name = "epiphany" tags = "main" master = "true"}
}

mouse
{
    root { button = "3" command = "spawn" args = {"exec urxvt"} }
    root { button = "4" command = "tag_viewnext" }
    root { button = "5" command = "tag_viewprev" }
    client { modkey = {"Mod4"} button = "1" command = "client_movemouse" }
    client { modkey = {"Mod4"} button = "2" command = "client_swap" args = {"0"} }
    client { modkey = {"Mod4"} button = "3" command = "client_resizemouse" }
    titlebar { button = "1" command = "client_movemouse" }
    titlebar { button = "3" command = "client_resizemouse" }
}

keys
{
    key { modkey = {"Mod4"} key = "F1" command = "spawn" args = {"for i in /usr/share/man/man?;do ls $i; done | cut -d. -f1 | awesome-menu -e 'urxvt -e man ' 'See manual page for:'"} }
    key { modkey = {"Mod4"} key = "F2" command = "spawn" args = {"find /usr/bin -type f -executable ! -empty | awesome-menu -e 'exec ' Execute:"} }
    key { modkey = {"Mod4"} key = "F3" command = "spawn" args = {"cut -d' ' -f1 ~/.ssh/known_hosts | cut -d, -f1 | awesome-menu -e 'urxvt -e ssh ' 'ssh to:'"} }
    key { modkey = {"Mod4"} key = "Return" command = "spawn" args = {"exec urxvt"} }
    key { modkey = {"Mod4"} key = "space" command = "tag_setlayout" args = {"+1"} }
    key { modkey = {"Mod4", "Shift"} key = "space" command = "tag_setlayout" args = {"-1"} }
    key { modkey = {"Mod4"} key = "b" command = "statusbar_toggle" }
    key { modkey = {"Mod4"} key = "j" command = "client_focus" args = {"+1"} }
    key { modkey = {"Mod4"} key = "k" command = "client_focus" args = {"-1"} }
    key { modkey = {"Mod4"} key = "Tab" command = "focus_history" args = {"-1"} }
    key { modkey = {"Mod4", "Shift"} key = "j" command = "client_swap" args = {"+1"} }
    key { modkey = {"Mod4", "Shift"} key = "k" command = "client_swap" args = {"-1"} }
    key { modkey = {"Mod4", "Control"} key = "j" command = "screen_focus" args = {"+1"} }
    key { modkey = {"Mod4", "Control"} key = "k" command = "screen_focus" args = {"-1"} }
    key { modkey = {"Mod4"} key = "h" command = "tag_setmwfact" args = {"-0.05"} }
    key { modkey = {"Mod4"} key = "l" command = "tag_setmwfact" args = {"+0.05"} }
    key { modkey = {"Mod4", "Shift"} key = "h" command = "tag_setnmaster" args = {"+1"} }
    key { modkey = {"Mod4", "Shift"} key = "l" command = "tag_setnmaster" args = {"-1"} }
    key { modkey = {"Mod4", "Control"} key = "h" command = "tag_setncol" args = {"+1"} }
    key { modkey = {"Mod4", "Control"} key = "l" command = "tag_setncol" args = {"-1"} }
    key { modkey = {"Mod4"} key = "Escape" command = "tag_prev_selected" }
    key { modkey = {"Mod4"} key = "Left" command = "tag_viewprev" }
    key { modkey = {"Mod4"} key = "Right" command = "tag_viewnext" }
    key { modkey = {"Mod4"} key = "m" command = "client_togglemax" }
    key { modkey = {"Mod4", "Control"} key = "Return" command = "client_swap" args = {"0"} }
    key { modkey = {"Mod4", "Control"} key = "space" command = "client_setfloating" }
    key { modkey = {"Mod4"} key = "s" command = "client_togglescratch" }
    key { modkey = {"Mod4", "Control"} key = "s" command = "client_setscratch" }
    key { modkey = {"Mod4"} key = "r" command = "client_redraw" }
    key { modkey = {"Mod4"} key = "F4" command = "client_kill" }
    key { modkey = {"Mod4", "Shift"} key = "q" command = "quit" }
    key { modkey = {"Mod4", "Control"} key = "r" command = "restart" }

    key { modkey = {"Mod4"} key = "0" command = "tag_toggleview" }
    key { modkey = {"Mod4", "Control"} key = "0" command = "tag_toggleview" }
    key { modkey = {"Mod4", "Control"} key = "1" command = "tag_toggleview" args = {"1"} }
    key { modkey = {"Mod4", "Control"} key = "2" command = "tag_toggleview" args = {"2"} }
    key { modkey = {"Mod4", "Control"} key = "3" command = "tag_toggleview" args = {"3"} }
    key { modkey = {"Mod4", "Control"} key = "4" command = "tag_toggleview" args = {"4"} }
    key { modkey = {"Mod4", "Control"} key = "5" command = "tag_toggleview" args = {"5"} }
    key { modkey = {"Mod4", "Control"} key = "6" command = "tag_toggleview" args = {"6"} }
    key { modkey = {"Mod4", "Control"} key = "7" command = "tag_toggleview" args = {"7"} }
    key { modkey = {"Mod4", "Control"} key = "8" command = "tag_toggleview" args = {"8"} }
    key { modkey = {"Mod4", "Control"} key = "9" command = "tag_toggleview" args = {"9"} }

    key { modkey = {"Mod4", "Shift"} key = "0" command = "client_tag" }
    key { modkey = {"Mod4", "Shift"} key = "1" command = "client_tag" args = {"1"} }
    key { modkey = {"Mod4", "Shift"} key = "2" command = "client_tag" args = {"2"} }
    key { modkey = {"Mod4", "Shift"} key = "3" command = "client_tag" args = {"3"} }
    key { modkey = {"Mod4", "Shift"} key = "4" command = "client_tag" args = {"4"} }
    key { modkey = {"Mod4", "Shift"} key = "5" command = "client_tag" args = {"5"} }
    key { modkey = {"Mod4", "Shift"} key = "6" command = "client_tag" args = {"6"} }
    key { modkey = {"Mod4", "Shift"} key = "7" command = "client_tag" args = {"7"} }
    key { modkey = {"Mod4", "Shift"} key = "8" command = "client_tag" args = {"8"} }
    key { modkey = {"Mod4", "Shift"} key = "9" command = "client_tag" args = {"9"} }

    key { modkey = {"Mod4", "Shift", "Control"} key = "0" command = "client_toggletag" }
    key { modkey = {"Mod4", "Shift", "Control"} key = "1" command = "client_toggletag" args = {"1"} }
    key { modkey = {"Mod4", "Shift", "Control"} key = "2" command = "client_toggletag" args = {"2"} }
    key { modkey = {"Mod4", "Shift", "Control"} key = "3" command = "client_toggletag" args = {"3"} }
    key { modkey = {"Mod4", "Shift", "Control"} key = "4" command = "client_toggletag" args = {"4"} }
    key { modkey = {"Mod4", "Shift", "Control"} key = "5" command = "client_toggletag" args = {"5"} }
    key { modkey = {"Mod4", "Shift", "Control"} key = "6" command = "client_toggletag" args = {"6"} }
    key { modkey = {"Mod4", "Shift", "Control"} key = "7" command = "client_toggletag" args = {"7"} }
    key { modkey = {"Mod4", "Shift", "Control"} key = "8" command = "client_toggletag" args = {"8"} }
    key { modkey = {"Mod4", "Shift", "Control"} key = "9" command = "client_toggletag" args = {"9"} }

## MINE ##
    key { modkey = {"Mod4"}             key = "grave"           command = "spawn" args = {"urxvt"} }
    key { modkey = {"Mod4"}             key = "1"           command = "spawn" args = {"epiphany"} }
    key { modkey = {"Mod4"}             key = "2"           command = "spawn" args = {"abiword"} }
    key { modkey = {"Mod4"}             key = "3"           command = "spawn" args = {"thunar"} }
    key { modkey = {"Mod4"}             key = "4"           command = "spawn" args = {"gimp"} }
    key { modkey = {"Mod4"}             key = "5"           command = "spawn" args = {"pidgin"} }


}
# vim: filetype=conf

```

But when I run amazing either nothing happens or I get this
```
/usr/lib/ruby/1.8/optparse.rb:1443:in `complete': invalid option: --verbose (OptionParser::InvalidOption)
    from /usr/lib/ruby/1.8/optparse.rb:1441:in `catch'
    from /usr/lib/ruby/1.8/optparse.rb:1441:in `complete'
    from /usr/lib/ruby/1.8/optparse.rb:1254:in `parse_in_order'
    from /usr/lib/ruby/1.8/optparse.rb:1247:in `catch'
    from /usr/lib/ruby/1.8/optparse.rb:1247:in `parse_in_order'
    from /usr/lib/ruby/1.8/optparse.rb:1241:in `order!'
    from /usr/lib/ruby/1.8/optparse.rb:1332:in `permute!'
    from /usr/lib/ruby/1.8/optparse.rb:1353:in `parse!'
    from /usr/lib/ruby/site_ruby/1.8/amazing/options.rb:28:in `parse'
    from /usr/lib/ruby/site_ruby/1.8/amazing/cli/helpers.rb:21:in `parse_options'
    from /usr/lib/ruby/site_ruby/1.8/amazing/cli.rb:47:in `run'
    from /usr/bin/amazing:19

```

---

### Post by Gigamo on 2008-05-14
I replied on the Arch forums to your similar thread :)

---

