---
title: "Counter Strike Source (CS:S) Dedicated server problems! need some help please!"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by GodsDead on 2007-12-06
Hey all!
i have had a look through many CS:S threads, cant realyl find why this is screwing up..
well i followed this tut:
[http://wolphination.com/linux/2006/03/29/how-to-setup-a-cssource-dedicated-server/](http://wolphination.com/linux/2006/03/29/how-to-setup-a-cssource-dedicated-server/)

and managed to get it all installed, apart from HLstats x, i skipped that step.
Running the server via terminal or shell i get these errors (ill post the whole log thing from when i run the server..)
```

root@Spicy:/home/tom/srcds_l# ./srcds_run -console -game cstrike +map cs_italy -autoupdate
Auto detecting CPU
Using SSE2 Optimised binary.
Server will auto-restart if there is a crash.
Updating server using Steam.
Checking bootstrapper version ...
Updating Installation
Checking/Installing 'Counter-Strike Source Shared Content' version 68


Checking/Installing 'Base Source Shared Models' version 4


Checking/Installing 'Base Source Shared Sounds' version 4


Checking/Installing 'Base Source Shared Materials' version 8


Checking/Installing 'Source Dedicated Server Linux' version 90


HLDS installation up to date

Console initialized.
Game.dll loaded for "Counter-Strike: Source"
maxplayers set to 32
Network: IP 127.0.1.1, mode MP, dedicated Yes, ports 27015 SV / 27005 CL
Executing dedicated server config file
Incorrect price blob version! Update your server!
ERROR: mp_dynamicpricing set to 1 but couldn't download the price list!
Error: Material "sprites/bubble" : proxy "AnimatedTexture" not found!
Section [Scenes]: 0 resources total 0 bytes, 0.00 % of limit (2.10 MB)
net.cpp (960) : Assertion Failed: 0 == iRet && iValLen == sizeof( iVal ) && cSendBufSize <= iVal
net.cpp (968) : Assertion Failed: 0 == iRet && iValLen == sizeof( iVal ) && cRecvBufSize <= iVal
Unknown command "sv_secure"
exec banned_user.cfg: file size larger than 20MB.
exec banned_ip.cfg: file size larger than 20MB.
Writing cfg/banned_user.cfg.
Writing cfg/banned_ip.cfg.
Server logging enabled.
Server logging data to file logs/L1206003.log
L 12/06/2007 - 16:59:51: Log file started (file "logs/L1206003.log") (game "/home/tom/srcds_l/cstrike") (version "3224")
L 12/06/2007 - 16:59:51: server_cvar: "mp_autoteambalance" "0"
L 12/06/2007 - 16:59:51: server_cvar: "mp_forcerespawn" "1"
L 12/06/2007 - 16:59:51: server_cvar: "mp_teamplay" "0"
L 12/06/2007 - 16:59:51: server_cvar: "mp_fraglimit" "0"
L 12/06/2007 - 16:59:51: server_cvar: "mp_maxrounds" "0"
L 12/06/2007 - 16:59:51: server_cvar: "mp_timelimit" "15"
L 12/06/2007 - 16:59:51: server_cvar: "mp_roundtime" "2.5"
L 12/06/2007 - 16:59:51: server_cvar: "mp_autocrosshair" "0"
L 12/06/2007 - 16:59:51: server_cvar: "mp_c4timer" "30"
L 12/06/2007 - 16:59:51: server_cvar: "mp_falldamage" "1"
L 12/06/2007 - 16:59:51: server_cvar: "mp_flashlight" "1"
L 12/06/2007 - 16:59:51: server_cvar: "mp_footsteps" "1"
L 12/06/2007 - 16:59:51: server_cvar: "mp_freezetime" "2"
L 12/06/2007 - 16:59:51: server_cvar: "mp_friendlyfire" "1"
L 12/06/2007 - 16:59:51: server_cvar: "mp_hostagepenalty" "4"
L 12/06/2007 - 16:59:51: server_cvar: "mp_limitteams" "2"
L 12/06/2007 - 16:59:51: server_cvar: "sv_footsteps" "1"
L 12/06/2007 - 16:59:51: server_cvar: "mp_weaponstay" "0"
L 12/06/2007 - 16:59:51: server_cvar: "decalfrequency" "10"
L 12/06/2007 - 16:59:51: server_cvar: "sv_specaccelerate" "5"
L 12/06/2007 - 16:59:51: server_cvar: "sv_specnoclip" "1"
L 12/06/2007 - 16:59:51: server_cvar: "sv_specspeed" "3"
L 12/06/2007 - 16:59:51: server_cvar: "sv_gravity" "800"
L 12/06/2007 - 16:59:51: server_cvar: "sv_friction" "4"
L 12/06/2007 - 16:59:51: server_cvar: "sv_airaccelerate" "10"
L 12/06/2007 - 16:59:51: server_cvar: "sv_stopspeed" "75"
L 12/06/2007 - 16:59:51: server_cvar: "sv_stepsize" "18"
L 12/06/2007 - 16:59:51: server_cvar: "sv_maxspeed" "320"
Unknown command "ma_war"
Console: Public Mode CFG executed
L 12/06/2007 - 16:59:51: "Console<0><Console><Console>" say "Public Mode CFG executed"
******     Executing mani_server.cfg      ****** 
Unknown command "mani_adverts"
Unknown command "mani_time_between_adverts"
Unknown command "mani_adverts_chat_area"
Unknown command "mani_adverts_top_left"
Unknown command "mani_advert_col_red"
Unknown command "mani_advert_col_green"
Unknown command "mani_advert_col_blue"
Unknown command "mani_advert_dead_only"
Unknown command "mani_adverts_bottom_area"
Unknown command "mani_stats"
Unknown command "mani_stats_mode"
Unknown command "mani_stats_drop_player_days"
Unknown command "mani_stats_calculate"
Unknown command "mani_stats_kills_required"
Unknown command "mani_stats_kills_before_points_removed"
Unknown command "mani_stats_top_display_time"
Unknown command "mani_stats_show_rank_to_all"
Unknown command "mani_stats_write_text_file"
Unknown command "mani_stats_calculate_frequency"
Unknown command "mani_stats_write_frequency_to_disk"
Unknown command "mani_stats_by_steam_id"
Unknown command "mani_stats_include_bot_kills"
Unknown command "mani_stats_decay_start"
Unknown command "mani_stats_decay_period"
Unknown command "mani_stats_decay_restore_points_on_connect"
Unknown command "mani_stats_points_add_only"
Unknown command "mani_stats_ignore_ranks_after_x_days"
Unknown command "mani_stats_points_multiplier"
Unknown command "mani_stats_points_death_multiplier"
Unknown command "mani_stats_css_weapon_ak47"
Unknown command "mani_stats_css_weapon_m4a1"
Unknown command "mani_stats_css_weapon_mp5navy"
Unknown command "mani_stats_css_weapon_awp"
Unknown command "mani_stats_css_weapon_usp"
Unknown command "mani_stats_css_weapon_deagle"
Unknown command "mani_stats_css_weapon_aug"
Unknown command "mani_stats_css_weapon_hegrenade"
Unknown command "mani_stats_css_weapon_xm1014"
Unknown command "mani_stats_css_weapon_knife"
Unknown command "mani_stats_css_weapon_g3sg1"
Unknown command "mani_stats_css_weapon_sg550"
Unknown command "mani_stats_css_weapon_galil"
Unknown command "mani_stats_css_weapon_m3"
Unknown command "mani_stats_css_weapon_scout"
Unknown command "mani_stats_css_weapon_sg552"
Unknown command "mani_stats_css_weapon_famas"
Unknown command "mani_stats_css_weapon_glock"
Unknown command "mani_stats_css_weapon_tmp"
Unknown command "mani_stats_css_weapon_ump45"
Unknown command "mani_stats_css_weapon_p90"
Unknown command "mani_stats_css_weapon_m249"
Unknown command "mani_stats_css_weapon_elite"
Unknown command "mani_stats_css_weapon_mac10"
Unknown command "mani_stats_css_weapon_fiveseven"
Unknown command "mani_stats_css_weapon_p228"
Unknown command "mani_stats_css_weapon_flashbang"
Unknown command "mani_stats_css_weapon_smokegrenade"
Unknown command "mani_stats_css_bomb_planted_bonus"
Unknown command "mani_stats_css_bomb_defused_bonus"
Unknown command "mani_stats_css_hostage_rescued_bonus"
Unknown command "mani_stats_css_hostage_killed_bonus"
Unknown command "mani_stats_css_vip_escape_bonus"
Unknown command "mani_stats_css_vip_killed_bonus"
Unknown command "mani_stats_css_ct_eliminated_team_bonus"
Unknown command "mani_stats_css_t_eliminated_team_bonus"
Unknown command "mani_stats_css_ct_vip_escaped_team_bonus"
Unknown command "mani_stats_css_t_vip_assassinated_team_bonus"
Unknown command "mani_stats_css_t_target_bombed_team_bonus"
Unknown command "mani_stats_css_ct_all_hostages_rescued_team_bonus"
Unknown command "mani_stats_css_ct_bomb_defused_team_bonus"
Unknown command "mani_stats_css_ct_hostage_killed_team_bonus"
Unknown command "mani_stats_css_ct_hostage_rescued_team_bonus"
Unknown command "mani_stats_css_t_bomb_planted_team_bonus"
Unknown command "mani_stats_dods_weapon_amerknife"
Unknown command "mani_stats_dods_weapon_spade"
Unknown command "mani_stats_dods_weapon_colt"
Unknown command "mani_stats_dods_weapon_p38"
Unknown command "mani_stats_dods_weapon_c96"
Unknown command "mani_stats_dods_weapon_garand"
Unknown command "mani_stats_dods_weapon_m1carbine"
Unknown command "mani_stats_dods_weapon_k98"
Unknown command "mani_stats_dods_weapon_spring"
Unknown command "mani_stats_dods_weapon_k98_scoped"
Unknown command "mani_stats_dods_weapon_thompson"
Unknown command "mani_stats_dods_weapon_mp40"
Unknown command "mani_stats_dods_weapon_mp44"
Unknown command "mani_stats_dods_weapon_bar"
Unknown command "mani_stats_dods_weapon_30cal"
Unknown command "mani_stats_dods_weapon_mg42"
Unknown command "mani_stats_dods_weapon_bazooka"
Unknown command "mani_stats_dods_weapon_pschreck"
Unknown command "mani_stats_dods_weapon_frag_us"
Unknown command "mani_stats_dods_weapon_frag_ger"
Unknown command "mani_stats_dods_weapon_smoke_us"
Unknown command "mani_stats_dods_weapon_smoke_ger"
Unknown command "mani_stats_dods_weapon_riflegren_us"
Unknown command "mani_stats_dods_weapon_riflegren_ger"
Unknown command "mani_stats_dods_weapon_punch"
Unknown command "mani_stats_dods_capture_point"
Unknown command "mani_stats_dods_block_capture"
Unknown command "mani_stats_dods_round_win_bonus"
Unknown command "mani_show_victim_stats"
Unknown command "mani_show_victim_stats_inflicted_only"
Unknown command "mani_player_settings_damage"
Unknown command "mani_stats_most_destructive"
Unknown command "mani_stats_most_destructive_mode"
Unknown command "mani_player_settings_destructive"
Unknown command "mani_tk_protection"
Unknown command "mani_tk_forgive"
Unknown command "mani_tk_spawn_time"
Unknown command "mani_tk_allow_bots_to_punish"
Unknown command "mani_tk_allow_bots_to_add_violations"
Unknown command "mani_tk_offences_for_ban"
Unknown command "mani_tk_ban_time"
Unknown command "mani_tk_slap_on_team_wound"
Unknown command "mani_tk_slap_on_team_wound_damage"
Unknown command "mani_tk_show_opposite_team_wound"
Unknown command "mani_tk_add_violation_without_forgive"
Unknown command "mani_tk_allow_forgive_option"
Unknown command "mani_tk_allow_blind_option"
Unknown command "mani_tk_blind_amount"
Unknown command "mani_tk_allow_slap_option"
Unknown command "mani_tk_allow_cash_option"
Unknown command "mani_tk_slap_to_damage"
Unknown command "mani_tk_cash_percent"
Unknown command "mani_tk_allow_freeze_option"
Unknown command "mani_tk_allow_drugged_option"
Unknown command "mani_tk_allow_burn_option"
Unknown command "mani_tk_burn_time"
Unknown command "mani_tk_allow_slay_option"
Unknown command "mani_tk_team_wound_reflect"
Unknown command "mani_tk_team_wound_reflect_threshold"
Unknown command "mani_tk_team_wound_reflect_ratio"
Unknown command "mani_tk_team_wound_reflect_ratio_increase"
Unknown command "mani_tk_allow_time_bomb_option"
Unknown command "mani_tk_time_bomb_seconds"
Unknown command "mani_tk_time_bomb_blast_radius"
Unknown command "mani_tk_time_bomb_show_beams"
Unknown command "mani_tk_time_bomb_blast_mode"
Unknown command "mani_tk_allow_fire_bomb_option"
Unknown command "mani_tk_fire_bomb_seconds"
Unknown command "mani_tk_fire_bomb_blast_radius"
Unknown command "mani_tk_fire_bomb_show_beams"
Unknown command "mani_tk_fire_bomb_blast_mode"
Unknown command "mani_tk_fire_bomb_burn_time"
Unknown command "mani_tk_allow_freeze_bomb_option"
Unknown command "mani_tk_freeze_bomb_seconds"
Unknown command "mani_tk_freeze_bomb_blast_radius"
Unknown command "mani_tk_freeze_bomb_show_beams"
Unknown command "mani_tk_freeze_bomb_blast_mode"
Unknown command "mani_tk_time_bomb_beep_radius"
Unknown command "mani_tk_fire_bomb_beep_radius"
Unknown command "mani_tk_freeze_bomb_beep_radius"
Unknown command "mani_tk_allow_beacon_option"
Unknown command "mani_tk_beacon_radius"
Unknown command "mani_reserve_slots"
Unknown command "mani_reserve_slots_number_of_slots"
Unknown command "mani_reserve_slots_kick_message"
Unknown command "mani_reserve_slots_redirect_message"
Unknown command "mani_reserve_slots_redirect"
Unknown command "mani_reserve_slots_allow_slot_fill"
Unknown command "mani_reserve_slots_kick_method"
Unknown command "mani_reserve_slots_include_admin"
Unknown command "mani_high_ping_kick"
Unknown command "mani_high_ping_kick_ping_limit"
Unknown command "mani_high_ping_kick_samples_required"
Unknown command "mani_high_ping_kick_message"
Unknown command "mani_adminslap_anonymous"
Unknown command "mani_adminblind_anonymous"
Unknown command "mani_adminfreeze_anonymous"
Unknown command "mani_adminteleport_anonymous"
Unknown command "mani_admindrug_anonymous"
Unknown command "mani_adminmap_anonymous"
Unknown command "mani_adminswap_anonymous"
Unknown command "mani_adminvote_anonymous"
Unknown command "mani_adminsay_anonymous"
Unknown command "mani_adminkick_anonymous"
Unknown command "mani_adminslay_anonymous"
Unknown command "mani_adminban_anonymous"
Unknown command "mani_adminburn_anonymous"
Unknown command "mani_adminnoclip_anonymous"
Unknown command "mani_adminmute_anonymous"
Unknown command "mani_admincash_anonymous"
Unknown command "mani_adminsetskin_anonymous"
Unknown command "mani_admindropc4_anonymous"
Unknown command "mani_admintimebomb_anonymous"
Unknown command "mani_adminfirebomb_anonymous"
Unknown command "mani_adminfreezebomb_anonymous"
Unknown command "mani_adminhealth_anonymous"
Unknown command "mani_adminbeacon_anonymous"
Unknown command "mani_admingravity_anonymous"
Unknown command "mani_chat_flood_time"
Unknown command "mani_chat_flood_message"
Unknown command "mani_autobalance_teams"
Unknown command "mani_autobalance_mode"
Unknown command "mani_military_time"
Unknown command "mani_thetime_timezone"
Unknown command "mani_adjust_time"
Unknown command "mani_voting"
Unknown command "mani_vote_dont_show_last_maps"
Unknown command "mani_vote_extend_time"
Unknown command "mani_vote_allow_extend"
Unknown command "mani_vote_allowed_voting_time"
Unknown command "mani_vote_allow_end_of_map_vote"
Unknown command "mani_vote_max_extends"
Unknown command "mani_vote_extend_rounds"
Unknown command "mani_vote_mapcycle_mode_for_random_map_vote"
Unknown command "mani_vote_mapcycle_mode_for_admin_map_vote"
Unknown command "mani_vote_time_before_end_of_map_vote"
Unknown command "mani_vote_max_maps_for_end_of_map_vote"
Unknown command "mani_vote_end_of_map_swap_team"
Unknown command "mani_vote_end_of_map_percent_required"
Unknown command "mani_vote_rcon_percent_required"
Unknown command "mani_vote_question_percent_required"
Unknown command "mani_vote_map_percent_required"
Unknown command "mani_vote_random_map_percent_required"
Unknown command "mani_vote_show_vote_mode"
Unknown command "mani_vote_dont_show_if_alive"
Unknown command "mani_vote_allow_user_vote_map"
Unknown command "mani_vote_allow_user_vote_map_extend"
Unknown command "mani_vote_allow_user_vote_kick"
Unknown command "mani_vote_allow_user_vote_ban"
Unknown command "mani_vote_extend_percent_required"
Unknown command "mani_vote_user_vote_map_percentage"
Unknown command "mani_vote_user_vote_map_time_before_vote"
Unknown command "mani_vote_user_vote_map_minimum_votes"
Unknown command "mani_vote_user_vote_kick_mode"
Unknown command "mani_vote_user_vote_kick_percentage"
Unknown command "mani_vote_user_vote_kick_time_before_vote"
Unknown command "mani_vote_user_vote_kick_minimum_votes"
Unknown command "mani_vote_user_vote_ban_mode"
Unknown command "mani_vote_user_vote_ban_percentage"
Unknown command "mani_vote_user_vote_ban_time_before_vote"
Unknown command "mani_vote_user_vote_ban_minimum_votes"
Unknown command "mani_vote_user_vote_ban_time"
Unknown command "mani_vote_user_vote_ban_type"
Unknown command "mani_vote_allow_rock_the_vote"
Unknown command "mani_vote_rock_the_vote_percent_required"
Unknown command "mani_vote_time_before_rock_the_vote"
Unknown command "mani_vote_rock_the_vote_number_of_nominations"
Unknown command "mani_vote_rock_the_vote_number_of_maps"
Unknown command "mani_vote_rock_the_vote_threshold_percent"
Unknown command "mani_vote_rock_the_vote_threshold_minimum"
Unknown command "mani_player_settings_vote_progress"
Unknown command "mani_filter_words_mode"
Unknown command "mani_filter_words_warning"
Unknown command "mani_sounds_per_round"
Unknown command "mani_sounds_filter_if_dead"
Unknown command "mani_sounds_auto_download"
Unknown command "mani_player_settings_sounds"
Unknown command "mani_log_mode"
Unknown command "mani_log_directory"
Unknown command "mani_show_death_beams"
Unknown command "mani_player_settings_death_beam"
Unknown command "mani_blind_ghosters"
Unknown command "mani_vote_allow_user_vote_ban_ghost"
Unknown command "mani_vote_allow_user_vote_kick_ghost"
Unknown command "mani_map_adverts"
Unknown command "mani_map_adverts_in_war"
Unknown command "mani_player_name_change_threshold"
Unknown command "mani_player_name_change_reset"
Unknown command "mani_player_name_change_punishment"
Unknown command "mani_player_name_change_ban_time"
Unknown command "mani_spawnpoints_mode"
Unknown command "mani_skins_admin"
Unknown command "mani_skins_public"
Unknown command "mani_skins_force_public"
Unknown command "mani_skins_setskin_misc_only"
Unknown command "mani_skins_auto_download"
Unknown command "mani_skins_reserved"
Unknown command "mani_skins_force_choose_on_join"
Unknown command "mani_skins_random_bot_skins"
Unknown command "mani_spray_tag"
Unknown command "mani_spray_tag_spray_duration"
Unknown command "mani_spray_tag_spray_distance_limit"
Unknown command "mani_spray_tag_spray_highlight"
Unknown command "mani_spray_tag_ban_time"
Unknown command "mani_spray_tag_warning_message"
Unknown command "mani_spray_tag_kick_message"
Unknown command "mani_spray_tag_ban_message"
Unknown command "mani_spray_tag_perm_ban_message"
Unknown command "mani_spray_tag_block_mode"
Unknown command "mani_spray_tag_block_message"
Unknown command "mani_spray_tag_slap_damage"
Unknown command "mani_warmup_timer"
Unknown command "mani_warmup_timer_show_countdown"
Unknown command "mani_warmup_timer_knives_only"
Unknown command "mani_warmup_timer_knives_respawn"
Unknown command "mani_warmup_timer_ignore_tk"
Unknown command "mani_warmup_timer_knives_only_ignore_fyi_aim_maps"
Unknown command "mani_warmup_timer_unlimited_grenades"
Unknown command "mani_warmup_timer_spawn_item_1"
Unknown command "mani_warmup_timer_spawn_item_2"
Unknown command "mani_warmup_timer_spawn_item_3"
Unknown command "mani_warmup_timer_spawn_item_4"
Unknown command "mani_warmup_timer_spawn_item_5"
Unknown command "mani_warmup_timer_disable_ff"
Unknown command "mani_warmup_infinite_ammo"
Unknown command "mani_use_amx_style_menu"
Unknown command "mani_sort_menus"
Unknown command "mani_external_stats_log"
Unknown command "mani_external_stats_log_allow_war_logs"
Unknown command "mani_external_stats_css_include_bots"
Unknown command "mani_save_scores"
Unknown command "mani_save_scores_tracking_time"
Unknown command "mani_save_scores_css_cash"
Unknown command "mani_team_join_force_auto"
Unknown command "mani_team_join_keep_same_team"
Unknown command "mani_steam_id_pending_timeout"
Unknown command "mani_steam_id_pending_show_admin"
Unknown command "mani_afk_kicker"
Unknown command "mani_afk_kicker_mode"
Unknown command "mani_afk_kicker_alive_rounds"
Unknown command "mani_afk_kicker_spectator_rounds"
Unknown command "mani_afk_kicker_alive_timer"
Unknown command "mani_afk_kicker_spectator_timer"
Unknown command "mani_afk_kicker_immunity_to_spec_only"
Unknown command "mani_css_betting"
Unknown command "mani_css_betting_dead_only"
Unknown command "mani_css_betting_pay_losing_bets"
Unknown command "mani_css_betting_announce_one_v_one"
Unknown command "mani_css_bounty"
Unknown command "mani_css_bounty_kill_streak"
Unknown command "mani_css_bounty_start_cash"
Unknown command "mani_css_bounty_survive_round_cash"
Unknown command "mani_css_bounty_kill_cash"
Unknown command "mani_css_bounty_ct_red"
Unknown command "mani_css_bounty_ct_green"
Unknown command "mani_css_bounty_ct_blue"
Unknown command "mani_css_bounty_ct_alpha"
Unknown command "mani_css_bounty_t_red"
Unknown command "mani_css_bounty_t_green"
Unknown command "mani_css_bounty_t_blue"
Unknown command "mani_css_bounty_t_alpha"
Unknown command "mani_css_objectives"
Unknown command "mani_automap"
Unknown command "mani_automap_map_list"
Unknown command "mani_automap_player_threshold"
Unknown command "mani_automap_include_bots"
Unknown command "mani_automap_timer"
Unknown command "mani_automap_set_nextmap"
couldn't exec mani_quake_sounds.cfg
Unknown command "mani_mapcycle_mode"
Unknown command "mani_unlimited_grenades"
Unknown command "mani_war_mode_force_overview_zero"
Unknown command "mani_cs_stacking_num_levels"
Unknown command "mani_use_ma_in_say_command"
Unknown command "mani_dead_alltalk"
Unknown command "mani_mute_con_command_spam"
Unknown command "mani_adminsay_top_left"
Unknown command "mani_adminsay_chat_area"
Unknown command "mani_adminsay_bottom_area"
Unknown command "mani_allow_chat_to_admin"
Unknown command "mani_ff_player_only"
Unknown command "mani_nextmap_player_only"
Unknown command "mani_timeleft_player_only"
Unknown command "mani_thetime_player_only"
Unknown command "mani_admin_burn_time"
Unknown command "mani_hostage_follow_warning"
Unknown command "mani_say_command_prefix"
Unknown command "mani_all_see_ma_rates"
Unknown command "mani_swap_team_score"
Unknown command "mani_old_style_menu_behaviour"
Unknown command "mani_menu_force_text_input_via_esc"
Unknown command "mani_admin_temp_ban_time_limit"
Unknown command "mani_anti_rejoin"
Unknown command "mani_weapon_restrict_refund_on_spawn"
Unknown command "mani_weapon_restrict_prevent_pickup"
Unknown command "mani_exec_default_file1"
Unknown command "mani_exec_default_file2"
Unknown command "mani_exec_default_file3"
Unknown command "mani_exec_default_file4"
Unknown command "mani_exec_default_file5"
Unknown command "mani_sb_observe_mode"
****** Finished executing mani_server.cfg ****** 
Adding master server 69.28.151.162:27011
Adding master server 72.165.61.190:27011
L 12/06/2007 - 16:59:55: World triggered "Round_Start"
Connection to Steam servers successful.
   VAC secure mode is activated.



```
The first problem i have is there are errors, the majority coming from mani admin plugin!
i found  this:
[http://www.mani-admin-plugin.com/index.php?option=com_content&task=view&id=55&Itemid=25](http://www.mani-admin-plugin.com/index.php?option=com_content&task=view&id=55&Itemid=25)

But that douse not make sence to me!???!

i find those files but have no idea what i need to do with them, by any chance is the tutorial i used like proper out of date?

apart from those hideous errors, the server starts, i don't think it updates to the main servers as when i search for the server, i cant see it at all..

although in LAN, i can join the game, im guessing the mani admin mod didn't work.. but for future reference if someone tells me what iv done drastically  wrong, how the hell do i setup myself as an admin?  i mean i am connected via lan aswell..
and i couldn't find nor could a search for "adminlist" in any of the directory's..

and i have set my ports up correctly, i think?
heres the ports!

        1  	VENT  	3784 [tcp]
	2 	steam 	27000 - 27015 [udp] (cs:s)
	3 	steam2 	27030 - 27039 [udp] (cs:s)
	4 	steamfriend 	1200 [udp] (cs:s)
	5 	WebDisk 	2077 - 2078 [tcp/upd]
	6 	CSHLTV 	27015 [udp] (cs:s)
	7 	CSHLTV2 	27020 [udp] (cs:s)
	8 	RCON 	27015 [tpc] (cs:s)
	9 	masterserver 	27011 [tcp/udp] (cs:s)

all ports fordward to the ubuntu gusty i have setup with everything installed (192.168.0.8)
And my web server runs (out) fine! (http - setup separately in my router)

I just put all teh ports i used in case anything clashes..

this would be ausom if someone could help me out thanks!
!!

---

### Post by jnelson74 on 2008-03-13
Hello, did you ever get this fixed?  I am having the same issue, If anyone would be so kind as to tell me what this fix is, It would be appreciated!!

---

### Post by jnelson74 on 2008-03-21
Pretty pls???

---

