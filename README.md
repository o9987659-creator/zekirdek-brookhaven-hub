# zekirdek-brookhaven-hub
This great brookhaven script
-- ZEKIRDEK PANEL v2 (Toggle + Drag + Minimize)

local player = game.Players.LocalPlayer
local UIS = game:GetService("UserInputService")

-- GUI
local gui = Instance.new("ScreenGui")
gui.Name = "ZekirdekPanel"
gui.Parent = player.PlayerGui

-- Ana Frame
local frame = Instance.new("Frame", gui)
frame.Size = UDim2.new(0, 330, 0, 320)
frame.Position = UDim2.new(0.5, -165, 0.5, -160)
frame.BackgroundColor3 = Color3.fromRGB(30,30,30)
frame.BorderSizePixel = 0
frame.Active = true
frame.Draggable = true

-- Üst Bar
local top = Instance.new("Frame", frame)
top.Size = UDim2.new(1,0,0,45)
top.BackgroundColor3 = Color3.fromRGB(0,170,0)
top.BorderSizePixel = 0

-- Başlık
local title = Instance.new("TextLabel", top)
title.Size = UDim2.new(1, -45, 1, 0)
title.Position = UDim2.new(0, 10, 0, 0)
title.BackgroundTransparency = 1
title.Text = "zekirdek"
title.Font = Enum.Font.GothamBold
title.TextSize = 18
title.TextColor3 = Color3.new(1,1,1)
title.TextXAlignment = Enum.TextXAlignment.Left

-- Küçült Butonu
local minimize = Instance.new("TextButton", top)
minimize.Size = UDim2.new(0,45,1,0)
minimize.Position = UDim2.new(1,-45,0,0)
minimize.Text = "-"
minimize.Font = Enum.Font.GothamBold
minimize.TextSize = 22
minimize.TextColor3 = Color3.new(1,1,1)
minimize.BackgroundTransparency = 1

-- Mini Buton (küçük tuş)
local mini = Instance.new("TextButton", gui)
mini.Size = UDim2.new(0,120,0,40)
mini.Position = UDim2.new(0.02,0,0.5,0)
mini.BackgroundColor3 = Color3.fromRGB(0,120,255)
mini.Text = "zekirdek"
mini.Font = Enum.Font.GothamBold
mini.TextSize = 14
mini.TextColor3 = Color3.new(1,1,1)
mini.Visible = false
mini.Active = true
mini.Draggable = true

-- Buton oluşturucu
local function createButton(text, y, callback)
    local btn = Instance.new("TextButton", frame)
    btn.Size = UDim2.new(0.9,0,0,42)
    btn.Position = UDim2.new(0.05,0,0,y)
    btn.BackgroundColor3 = Color3.fromRGB(0,120,255)
    btn.BorderSizePixel = 0
    btn.Text = text
    btn.Font = Enum.Font.Gotham
    btn.TextSize = 14
    btn.TextColor3 = Color3.new(1,1,1)

    btn.MouseButton1Click:Connect(callback)
end

-- HUB BUTONLARI
createButton("Sander Hub", 60, function()
    loadstring(game:HttpGet("https://rawscripts.net/raw/Brookhaven-RP-New-Sander-XY-OP-Brookhaven-Script-Xmas-Uptade-No-Key-80608"))()
end)

createButton("Rot Hub", 110, function()
    loadstring(game:HttpGet("https://rawscripts.net/raw/Brookhaven-RP-Ro*o-Hub-BROOKHAVEN-80979"))()
end)

createButton("Chachado Hub", 160, function()
    loadstring(game:HttpGet("https://rawscripts.net/raw/Brookhaven-RP-Chachado-hub-77631"))()
end)

createButton("Vyron Hub", 210, function()
    loadstring(game:HttpGet("https://rawscripts.net/raw/Brookhaven-RP-Vyron-hub-81177"))()
end)

createButton("Phantom Hub", 260, function()
    loadstring(game:HttpGet("https://rawscripts.net/raw/Brookhaven-RP-Phantom-Client-80577"))()
end)

-- Küçült / Aç
minimize.MouseButton1Click:Connect(function()
    frame.Visible = false
    mini.Visible = true
end)

mini.MouseButton1Click:Connect(function()
    frame.Visible = true
    mini.Visible = false
end)

-- INSERT ile aç / kapat
UIS.InputBegan:Connect(function(input, gp)
    if gp then return end
    if input.KeyCode == Enum.KeyCode.Insert then
        frame.Visible = not frame.Visible
        mini.Visible = false
    end
end)
