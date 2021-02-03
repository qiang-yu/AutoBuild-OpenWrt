# AutoBuild-OpenWrt

Build OpenWrt firware [Lean's OpenWrt](https://github.com/coolsnowwolf/lede) using GitHub Actions  
Hereby thank P3TERX for his amazing job: https://github.com/P3TERX/Actions-OpenWrt/  

Hereby thank KFERMercer for his amazing job: https://github.com/KFERMercer/OpenWrt-CI  
You could edit and enable "Sync Code" YAML file to let your forked repo keep updated.

## 说明：这是自用的 OpenWrt 编译
**1. Prerequisite**
  - Sign up for [GitHub Actions](https://github.com/features/actions/signup)
  - Fork [this GitHub repository](https://github.com/esirplayground/AutoBuild-OpenWrt)
    
**2. Compile Firmware**
  - Click `[.github/workflows]` folder on the top of repo and you could see few workflow files, Each for one particular architecture(device).
  - Edit the workflow file you desire，uncomment push section 3 lines together and submit the commit.(Other 2 methods wait you to discover)
  - The build starts automatically. Progress can be viewed on the Actions page.
  - When the build is complete, click the `Artifacts` button in the upper right corner of the Actions page to download the binaries.
  - Default Web Admin IP: `192.168.2.90`, username `root`，password `password`

**3. Sync Code**
  - Uncomment 'push-branches-master' 3 lines under **`On`** section and commit changes to let the script sync the code once for you.
  - Uncomment 'schedule-cron' 2 lines under **`On`** section and commit changes to let the script sync the code everyday on 3 am[UTC +8]

**4. 怎么获得你想要的配置 .config 文件**
  - git clone https://github.com/coolsnowwolf/lede openwrt 
  - cd openwrt
  - echo "src-git infinityfreedom https://github.com/xiaoqingfengATGH/luci-theme-infinityfreedom.git" >> feeds.conf.default 
  - ./scripts/feeds update -a  
  - ./scripts/feeds install -a    
  - git clone https://github.com/fw876/helloworld.git package/shadowsocks-plus  
  - make clean
  - make menuconfig
  - 把生成的 .config 文件复制到这个工程，就可以让 github action 自动编译了   