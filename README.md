# roblox-teleport-gui
Script
local player = game.Players.LocalPlayer
local savedCFrame = nil

-- GUI
local gui = Instance.new("ScreenGui")
gui.Name = "TeleportGui"
gui.Parent = player:WaitForChild("PlayerGui")

local saveBtn = Instance.new("TextButton")
saveBtn.Size = UDim2.fromScale(0.25, 0.08)
saveBtn.Position = UDim2.fromScale(0.05, 0.8)
saveBtn.Text = "Save Position"
saveBtn.BackgroundColor3 = Color3.fromRGB(60, 180, 75)
saveBtn.TextScaled = true
saveBtn.Parent = gui

local tpBtn = Instance.new("TextButton")
tpBtn.Size = UDim2.fromScale(0.25, 0.08)
tpBtn.Position = UDim2.fromScale(0.35, 0.8)
tpBtn.Text = "Teleport"
tpBtn.BackgroundColor3 = Color3.fromRGB(70, 130, 255)
tpBtn.TextScaled = true
tpBtn.Parent = gui

-- Save position
saveBtn.MouseButton1Click:Connect(function()
	local char = player.Character
	if char and char:FindFirstChild("HumanoidRootPart") then
		savedCFrame = char.HumanoidRootPart.CFrame
	end
end)

-- Teleport
tpBtn.MouseButton1Click:Connect(function()
	local char = player.Character
	if savedCFrame and char and char:FindFirstChild("HumanoidRootPart") then
		char.HumanoidRootPart.CFrame = savedCFrame
	end
end)
