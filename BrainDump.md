# Squad Management Bot

## Functions

- Lookup - Player Lookup
  - Accepts playerName OR Steam 64 ID
  - This will search for a user and find their ID. It is specifically tied to the username or steam 64 id.
  - If multiple players are located, it will display a set of selection options with number selections
  - For multiple players !lookup #X to select number
  - When a single user is selected, it will invoke !playerinfo
- Player Info - print player info
  - Accepts Steam 64 ID
  - Displays the users first and last seen, total time registered in ALL servers OR specific server
  - Displays alternate usernames if available
  - Show if user is whitelisted. If whitelisted, also show which, if any, group the user is assigned too.
  - Sub option for TK count? This probably won't exist
- Server List - Lookup all servers associated with org.
  - Display all servers with an associated tiny int (#1, #10, etc)
  - Show player count
- Server Info - Display Server Info
- Server Seed Map - Set server to seed map
  - Accepts (Opt: Map Name) (Addl Opt: T1) (Addl Opt: T2)
  - Check for server player count, ensure under config setting (likely 10)
  - Map name optional, random selected otherwise
  - T1 and T2 optional. If one or both are left out it is selected at random in place of the missing one(s)
  - Always CombinedArms as per Seed standard, no option there. We'll include a list of "valid" combos for those that may need it
- Whitelist Lookup - Display if a user has whitelist
  - Displays if a user has a whitelist
- Add whitelist - Add a user or group to whitelist
  - Accepts Steam 64 ID, Group Name, or Group ID
  - Add one user or entire group to whitelist
  - If group, add to a new section in the remote admin config list (for whitelist import)
- Remove whitelist - Remove a user or group from whitelist
  - Accepts Steam 64 ID, Group Name, or Group ID
  - Remove one user OR entire group from whitelist.
  - Group removal will only remove the users WITHIN the group block. This is intentional so it can leave users who have WL separate of their group along with their group. We don't want to remove them from their individual WL status.
- Add Group - Add a new group
  - Requires: Group Name. Optional: Comments/additional info
  - This adds a group which can be used to WL a whole group (For example, QG), which allows for easy removal later
- Remove Group - Removes a group and removes WL from that group
  - Requires: Group Name or Group ID
  - Remove a group. If the group is in WL, the entire group is delisted from WL UNLESS a user is specifically added in a single user fashion (For example, add user Road-Block, add to 9A, WL 9A, remove WL for 9a, Road-Block remains whitelisted. If Road-Block were added to 9A WITHOUT a single user WL, he would be removed)
- Add to group - Adds a user to Group
  - Requires: Steam 64 ID, Group Name or Group ID.
- Remove from group - Remove from group.
  - Requires: Steam 64 ID, Group Name or Group ID

## Discord Commands

- !lookup playerName/steam64Id (Opt: Server ID [as # from !serverList or server ID from BM]) - Calls player lookup
- !playerinfo Steam64ID (Opt: Server ID [as # from !serverList or server ID from BM]) - Calls player info
- !serverlist - List SZ servers (by group/org) - Calls server list
- !serverInfo ServerId (# from !serverList OR BM ID, limited to SZ servers) - Call server info
- !seed (Opt: Map Name) (Addl Opt: T1 faction) (Addl Opt: T2 faction) - Call Server Seed Map.
- !whitelist - Whitelist related commands
  - add Steam64ID/groupId ServerId (from server list or BM ID). Comment (Username, reason to add, etc) - Calls Whitelist Add
  - rem/remove/del/delete Steam64ID ServerId (from server list or BM ID). - Calls Whitelist Remove
- !group - Group related commands
  - add Name - Create a new group with name via group add function
  - rem/remove/del/delete - Remove group via group remove function. This deleted any WL added via group add command.
  - user add - Add users
  - user rem/remove/del/delete - Remove a user from group
