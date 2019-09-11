
# UnityMMO
A lot of things are not good at working projects (such as ECS), so I have this project. I plan to make a 3D-MMO game from scratch in my spare time. Although most of the functions have been touched, I want to change the practice, otherwise It's not fun. The front-end gameplay system uses c#, the interface is developed with lua. The backend uses skynet.

For detailed design and progress, see: [Wiki](https://github.com/liuhaopen/UnityMMO/wiki "Wiki")

# Usage
Clone the project: ```git clone https://github.com/liuhaopen/UnityMMO.git --recurse```

Frontend:  

After downloading, the entire directory is the project directory of Unity, open it with Unity, run the main.unity scene to enter the login interface of the game.

Note: Since the game resources are too large and often changed (each version of the resource will be saved in the .git folder, clone will take a long time), so put it in another project management, in [UnityMMO-Resource](https://github.com/liuhaopen/UnityMMO-Resource/tree/master/Assets/AssetBundleRes "UnityMMO-Resource") Download the files and copy the Assets/AssetBundleRes and their meta files into the Assets directory of the project (note: some The plugin was not uploaded due to copyright issues. See the purchase link from the download-page.)

Backend:  

Install a virtual machine, I use CentOS7, then set the entire project directory to the shared directory of the virtual machine, cd to the Server directory and compile skynet: [skynet home page](https://github.com/cloudwu/skynet "skynet Home")

Install mysql (or MariaDB) on the virtual machine and import both database files located in `Server/data/`

Run: ```./run.sh``` to Run the server (if you want to extract the Server directory separately to other machines, remember to copy the Config, Proto, Common directories in UnityMMO/Lua and maintain the directory hierarchy. )

# Status & Prerequisites
```
Unity version: 2019.1.4f1
Platforms:
Client is for Windows and Android(should also support iOS, but I haven't tested);
Server is only for Linux;
```

# Recent GIF
19.07.03: Initially realized automatic pathfinding to find npc dialogue and Daguai two tasks:  
![GIF1](https://github.com/liuhaopen/ReadmeResources/blob/master/UnityMMO/auto_talk_and_fight.gif?raw=true)  
19.07.10: Add a copy scene:
![GIF2](https://github.com/liuhaopen/ReadmeResources/blob/master/UnityMMO/change_scene.gif?raw=true)
19.07.31: Initial completion of the backpack and GM system

19.08.11: Initial completion of the skill component based on the action component, see Server/lualib/Action and FightMgr, Hurt and PickTarget.lua

19.08.13: Complete the resurrection process

19.08.28: I have recently tested on mobile phones, optimizing one wave: camera operation, resource preloading, object pooling, and using the AutoLOD plugin to generate two levels of simple mode for each scene node (in fact, many models are at the farthest point) It can be replaced by a patch, that is, the bulletin board is always facing the camera, but even if there is no art resource, the tree has deleted a lot of tens of thousands of triangles. Light baking was changed to use Distance ShadowMask, near real-time shadow map. I can run it smoothly on my junk phone for the time being.
